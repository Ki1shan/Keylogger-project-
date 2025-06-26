# Stealth Keylogger with Remote Logging

>  **DISCLAIMER:**  
This project is created strictly for educational purposes and ethical cybersecurity learning.  
**Do not** run this software on any system without explicit permission. Unauthorized use is illegal.

---

## Overview

This Python script implements a basic **stealth keylogger** that:
- Runs silently in the background as a daemon.
- Captures all keyboard inputs.
- Sends the keystrokes to a remote TCP server in real time.

---

## How It Works

1. **Daemonization**:  
   The script forks itself and detaches from the terminal using `os.fork()` and `os.setsid()`, making it a background process.

2. **Silencing Output**:  
   It redirects both `stdout` and `stderr` to `/dev/null` to suppress any visible output.

3. **Remote Communication**:  
   A socket connection is attempted to the IP on port `3434`.  
   If successful, the client sends every key pressed to this remote server.

4. **Key Logging**:  
   Using the `pynput` library, the script listens for all keyboard events. Each key press (character or special key) is captured and sent through the socket.

---

## Code Execution

### 🔧 Prerequisites
- Python 3.x
- `pynput` module:  
  Install with: pip install pynput
- Run the Script: python3 keylogger.py

The program will:

- Print an initial message
- Fork and run in the background
- Attempt to connect to listeners IP
- Begin logging keys and sending them remotely

Server-Side Setup (For Testing)
To test the remote keylogging, run a listener on the remote machine: nc -lvp 3434

Security and Ethics:
- Use only in test environments or virtual machines you control.
- Never deploy this on other systems or networks without proper authorization.
- This script is intended to understand background processing, remote sockets, and ethical keylogging principles.


