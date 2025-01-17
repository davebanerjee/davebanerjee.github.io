---
layout:               post
title:                "Automatic Stretch Reminder"
subtitle:             "I wrote a script that reminds me to stretch every hour"
date:                 2025-01-16 00:53:56 -0500
last_modified_at:     2025-01-16 00:53:56 -0500
readable_date:        16 Jan 2026
permalink:            /blog/stretch-reminder
image:                /assets/stretch-reminder/stretch_reminder.png # image dimensions: 1000 × 668
image_desc:           Stretch reminder
read_time:            1 min read
featured:             false
comments:             true
---

**This is a low effort post. I wanted to publish as fast as possible.**

# Stretch Reminder

I've been sitting a lot lately. Recently, my back has been hurting, and I suspect the pain is coming from sitting statically for prolonged periods of time. To encourage me to move around more, I (mostly [Claude](https://claude.ai)) wrote a script that reminds me every hour to stretch (and to drink water). The code only works on MacOS, so if you are using another operating system, please copy paste this whole post into an LLM, tell it your operating system, and do what it says. Most likely, the LLM will guide you to create a CronJob or something. If the program isn't working, please [email me](mailto:dave.banerjee1@gmail.com).

![Stretch reminder](/assets/stretch-reminder/stretch_reminder.png)

A screenshot of the full-screen stretch reminder.
{:.figcaption}

The Python script creates a full-screen reminder application that interrupts work every hour, while the accompanying plist file ensures this reminder runs automatically every hour (you can change the frequency if you'd like). The .py file can go anywhere, but I placed the script under the directory ~/scripts. The .plist file **must** be placed under the directory ~/Library/LaunchAgents. 

Make sure to edit the .plist file to include the path to your .py file and the path to your Python interpreter (run `which python3` in your terminal to determine your Python interpreter path).

After saving the files, open your terminal, and run 

`launchctl load ~/Library/LaunchAgents/com.user.stretchreminder.plist`

~~~py
# file: "~/scripts/sretch_reminder.py"
import tkinter as tk
from datetime import datetime

class StretchReminder:
    def __init__(self):
        self.root = tk.Tk()
        self.root.title("Time to Stretch!")
        
        # Configure the window
        screen_width = self.root.winfo_screenwidth()
        screen_height = self.root.winfo_screenheight()
        self.root.geometry(f"{screen_width}x{screen_height}+0+0")
        self.root.lift()
        self.root.attributes("-topmost", True)
        self.root.attributes("-fullscreen", True)
        self.root.attributes("-alpha", 0.95)
        
        # Create main frame and content container
        main_frame = tk.Frame(self.root, bg='black')
        main_frame.pack(fill='both', expand=True)
        content_frame = tk.Frame(main_frame, bg='black')
        content_frame.place(relx=0.5, rely=0.5, anchor='center')
        
        # Current time
        tk.Label(
            content_frame,
            text=datetime.now().strftime("%I:%M %p"),
            font=("Helvetica", 48, "bold"),
            fg="white",
            bg="black"
        ).pack(pady=30)
        
        # Message
        tk.Label(
            content_frame,
            text="Time to stretch and drink water!",
            font=("Helvetica", 42),
            fg="white",
            bg="black",
            justify="center"
        ).pack(pady=40)
        
        # Dismiss button
        tk.Button(
            content_frame,
            text="Done! (Dismiss)",
            command=self.root.destroy,
            font=("Helvetica", 24),
            bg="white",
            fg="black",
            padx=30,
            pady=15
        ).pack(pady=40)
        
        # Bindings
        self.root.bind('<Escape>', lambda e: self.root.destroy())
        self.root.bind('<Button-1>', lambda e: self.root.destroy())

if __name__ == "__main__":
    app = StretchReminder()
    app.root.mainloop()
~~~

~~~xml
<!-- file: "~/Library/LaunchAgents/com.user.stretchreminder.plist" -->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.user.stretchreminder</string>
    <key>ProgramArguments</key>
    <array>
        <!-- Path to Python interpreter (assuming Anaconda's Python installation).
        Make sure to replace the path below with your Python interpreter.
        You can determine your interpreter by running `which python3` in your terminal.) -->
        <string>/Users/davebanerjee/anaconda3/bin/python3</string>
        <!-- Path to the stretch reminder script.
        This script can be located anywhere in your file system
        but make sure to update the path below accordingly-->
        <string>/Users/davebanerjee/scripts/stretch_reminder.py</string>
    </array>
    <key>StartCalendarInterval</key>
    <dict>
        <key>Minute</key>
        <integer>0</integer>
    </dict>
    <key>RunAtLoad</key>
    <true/>
</dict>
</plist>
~~~
