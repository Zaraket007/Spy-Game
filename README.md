📱 Android Remote Administration & Monitoring Tool
📖 Project Overview
This project demonstrates a dual-component remote administration system consisting of an Android Client Application and a Python Flask Control Dashboard.

The system establishes a local HTTP server (NanoHTTPD) directly on the Android device, allowing it to receive REST API commands. A centralized Flask server acts as a Command & Control (C2) dashboard, relaying user commands from a web interface to the device and rendering the results (text, JSON, or media files).

This tool is designed for educational purposes, security research, and authorized device management.

🚀 Key Features
1. Information Retrieval
The application can query internal Android content providers to extract sensitive user data in real-time:

📇 Contact Extraction: Retrieve the full list of saved contacts.

💬 SMS Dump: Fetch SMS message history.

📞 Call Logs: Export incoming, outgoing, and missed call history.

📋 Clipboard Monitor: Read the current text stored in the system clipboard.

2. Device Tracking & Monitoring
📍 GPS Location: Fetches the device's precise location coordinates.

🎙️ Remote Audio Recording: Triggers the microphone to record audio in the background and streams the .3gpp file back to the server.

📹 Remote Video Capture:

Dual-Camera Support: capable of initializing recording on either the Front or Back camera.

Background Operation: Records footage while the app is in the background.

File Transfer: Automatically uploads the recorded .mp4 file to the server upon stopping the recording.

3. System Control
💻 Shell Execution: A powerful feature that allows the server to send raw shell commands to the Android device and receive the standard output (stdout), effectively granting a remote terminal interface.

🛠️ Technical Architecture
Android Client (Kotlin)
NanoHTTPD: Runs a lightweight HTTP server on port 1234 within the Android device to listen for incoming commands.

Foreground Service: Implements a persistent notification and Service architecture to ensure the server remains active even when the app is minimized or the screen is off.

Heartbeat/Polling: Uses OkHttp and Coroutines to periodically register the device's local IP address with the Python server, ensuring connectivity even if the local IP changes.

Web Server (Python Flask)
Command Relay: Acts as the bridge between the web UI and the Android device.

Device Registration: Dynamic endpoint (/register) to handle incoming connections from mobile clients.

Media Handling: Special handling for binary file downloads (Audio/Video) ensuring correct MIME types (audio/3gpp, video/mp4) are served to the browser.

Web Interface: A clean, responsive dashboard (HTML/CSS/JS) for executing commands with a single click.
