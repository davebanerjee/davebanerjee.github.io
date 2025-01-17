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

**This is a low effort post written almost exclusively by [Claude](https://claude.ai). I wanted to publish as fast as possible. Please excuse the weird style of writing.**

# Stretch Reminder

While maintaining "good posture" has long been emphasized as crucial for physical health, recent research suggests that the traditional concept of perfect posture - sitting or standing ramrod straight for extended periods - may not be as beneficial as once thought. Our bodies are designed for movement, and holding any single position for too long, even if it's technically "correct," can lead to muscle fatigue, reduced circulation, and increased pressure on specific joints and tissues.

What appears to be more important for musculoskeletal health is frequent movement and postural variation throughout the day. This might mean alternating between sitting, standing, and walking; shifting between different sitting positions; or even occasionally adopting positions that might not fit the classical definition of good posture. **The key is to avoid static positioning, as movement helps nourish our joints, maintain muscle flexibility, and promote better blood flow**. This dynamic approach to posture aligns better with our evolutionary history as humans who were constantly moving rather than maintaining fixed positions for hours at a time.

To help me move around more, I wrote some code to remind me to stretch every hour (Note: this code only works on MacOS. If you are using another operating system, please copy paste this whole post into an LLM and do what it says. Most likely, the LLM will guide you to create a CronJob or something). The Python script creates a full-screen reminder application that interrupts work every hour, while the accompanying plist file ensures this reminder runs automatically every hour.

![Stretch reminder](/assets/stretch-reminder/stretch_reminder.png)

A screenshot of the full-screen stretch reminder.
{:.figcaption}

The Python script can go anywhere, but I placed the script at ~/scripts/stretch_reminder.py. The .plist file must be placed under the directory ~/Library/LaunchAgents. After creating the files, open your terminal of choice, and run 

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
