---
layout:               post
title:                "Confidential and Integrity-Protected File Storage System"
subtitle:             "I built file storage system that maintains confidentiality and integrity protection through encryption and hashing."
date:                 2023-10-14 00:51:56 -0500
last_modified_at:     2023-10-14 00:51:56 -0500
readable_date:        14 Oct 2023
permalink:            /projects/encrypted-file-storage
image:                /assets/encrypted-file-storage/locked_computer.jpeg
image_desc:           Computer with combinational lock
read_time:            
project:              true
---

# File Storage System with Data Privacy and Integrity Protection

I created a command line utility that allows users to encrypt files and store them into an archive (single binary file). This binary file ensures confidentiality through AES-CBC encryption and integrity through HMAC.

This project was inspired by a similar programming assignment in Security I at Columbia. I thought the idea of building a file storage system was really cool and wanted to explore confidentiality, integrity, encryption, and hashing in more depth on my own!

[**You can find the github repository here!**](https://github.com/davebanerjee/encypted-file-storage-system)

## Usage

    Usage: ./cstore <function> [-p password] archivename <files>
    <function> can be: list, add, extract.
    
    Example Usage:
    ./cstore list archivename
    ./cstore add [-p password] archivename file
    ./cstore extract [-p password] archivename file
    
    Options:
        -h, --help		 Show this help message.
        -p <PASSWORD>		 Specify password (plaintext) in console. If not supplied, user will be prompted.
    
    Note: file names must not exceed 20 characters. There can be more than one file. Files can be added to a pre-existing archive (i.e., './cstore add' can be called multiple times on different files).


## Security of Archive

### File Encryption

An active attacker will not be able to determine the contents of the files since each file is AES-CBC encrypted, and only the receiver can decrypt the file with a shared password. I used AES-CBC encryption (as opposed to AES-ECB or other deterministic encryption algorithms) so that each file in the archive is encrypted in a different way because of the randomness induced by the IV generated in the CBC algorithm.

### Integrity Protection

Integrity protection is ensured by taking the HMAC of the archive starting from byte 40 (where NUM_FILES begin). The generated signature must match the signature stored in the archive. If the signatures are different, then the file has been tampered with. We consider three cases:

1. If the hacker tampers any data after byte 40, then the generated signature will definitely be different than the signature within the archive. The hacker could also tamper with the signature stored within the archive, but they would be unable to find a matching signature without the shared password.
2. If the hacker tampers the first 8 bytes (MAGIC), then we will know that the message has been tampered because we do a direct strcmp to confirm that the first 8 bytes of the archive is the MAGIC number ("./cstore").
3. If the hacker tampers the signature (8-40 byte mark within the archive), then the generated signature of the rest of the file will not match the recently tampered signature.

Thus, our file storage system protects integrity.

## Archive Structure 

The archive has the following structure:

| Archive File      |
| :---------------: |
| MAGIC (8)         |
| SIGNATURE (32)    |
| NUM_FILES (4)     |
| FILE_NAME_1 (20)  |
| FILE_SIZE_1 (8)   |
| FILE_IV_1 (16)    | 
| FILE_DATA_1 (N_1) |
| FILE_NAME_2 (20)  |
| FILE_SIZE_2 (8)   |
| FILE_IV_2 (16)    |
| FILE_DATA_2 (N_2) |
| ...               |

- **MAGIC (8 BYTES):** This field is the string './cstore' that confirms that the file is an archive file.
- **SIGNATURE (32 BYTES):** This field is the HMAC of the rest of the archive file (i.e., HMAC of archive starting from byte 40 to the end). This signature ensures the message receiever can identify whether the archive has been tampered with.
- **NUM_FILES (4 BYTES):** This field holds an unsigned int that indicates the number of files stored in the archive. 
- **FILE_NAME_1 (20 BYTES):** This field holds the file name of the first file stored in the archive. If the file is less than 20 characters long, the remaining bytes in the field are padded with '\0'
- **FILE_SIZE_1 (8 BYTES):** This field holds an unsigned long long int that indicates the size of the first file in bytes.
- **FILE_IV_1 (16 BYTES):** This field holds the IV used for encrypting/decrypting the first file in storage
- **FILE_DATA_1 (N BYTES):** This field holds the encrypted file data. This field can be decrypted using the shared password and the given IV.
- Repeat the previous 4 bullets for every additionally file stored in the archive.

## CStoreObject

I designed the CStoreObject to populate variables that contain the archive name, password, signature, number of files, file names, file sizes, and the data of each encrypted file (including IV and ciphertext). If the archive already exists, then when creating the CStoreObject, the archive is read and the variables are populated. If the archive does NOT already exist, then when creating the CStoreObject, the CStoreArgs args is read and the CStoreObject variables are populated.

The function calculate_new_signature calculates the signature for an archive by generating the HMAC of all the data in the archive starting from byte 40 (this is where num_files begins in the archive structure).

## Algorithm for Adding Files to Archive

1. Check if archive already exists 
    - If archive does not exist: 
        1. Create archive file
        2. Add magic number (”./cstore”)
        3. Add num_files
    - If archive DOES exist: 
        1. Read through existing archive and populate CStoreObject
        2. Remove existing archive from current working directory
2. Loop through files
    1. Add file name
    2. Add file size
    3. Encrypt file data using AES-CBC, which will generate IV and encrypted data
    3. Add file IV and file ciphertext
3. After files have been added, we compute CStore signature by taking HMAC of the archive starting from byte 40
4. Create archive file and populate using information from the newly populated CStoreObject

## Algorithm for Listing and Extracting Files in Archive

The algorithm is very similar to the algorithm for add. The only difference is that rather than populating our CStoreObject with data from CStoreArgs args, we populate our CStoreObject by reading the pre-existing archive. When extracting, we create the named file in the current working directory and populate with the decrypted file data. When listing, we simply list the name of every file stored in the archive.

## Credits

This project was inspired by a homework assignment in COMS 4181 Security I at Columbia University. [All hashing and encryption functions were borrowed from Brad Conte](https://github.com/B-Con/crypto-algorithms). The code for parsing command line arguments was given in the initial assignment.

**I was responsible for writing AES-CBC algorithm, HMAC algorithm, CStoreObject, and CStore algorithm.**