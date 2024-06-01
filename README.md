# FileSharing

## Overview
This file sharing application allows users to easily share files from their desktop over a local network using an HTTP server. The application sets up a simple HTTP server on a specified port and generates a QR code containing the server's URL, which can be scanned to access the shared files.

Features
Simple HTTP server for sharing files from the desktop.
Automatic generation of a QR code for easy access to the server URL.
Cross-platform support (works on Windows, macOS, and Linux).
changes should be made for respective platform e.g. in macOS Replace os.environ['USERPROFILE'] with os.path.expanduser('~') to get the user's home directory.
Added s.close() after getting the IP address to close the socket properly.

changing the directory to access the files desktop with the help of os module
desktop = os.path.join(os.path.expanduser('~'), 'Desktop')
os.chdir(desktop)
finding the IP address of the PC
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.connect(("8.8.8.8", 80))
IP = "http://" + s.getsockname()[0] + ":" + str(PORT)
s.close()
link = IP

Requirements
Python 3.x
Required Python libraries:
http.server
socket
socketserver
webbrowser
pyqrcode
pypng
os

Installation
Ensure Python 3.x is installed on your system.
Install the required Python libraries using pip:

pip install pyqrcode
pip install pypng

Copy the provided script into a Python file, e.g., file_sharing_app.py.
Run the script using Python:

python file_sharing_app.py
The script will:

Set up an HTTP server on port 8010.
Generate a QR code containing the server's URL.
Open the QR code image in the default web browser.
On successful execution, the terminal will display:

The port on which the server is running.
The URL to be entered in the browser to access the shared files.
Instructions to use the generated QR code.
Scan the QR code with a mobile device to open the server URL in a web browser.


Script Explanation
Importing necessary modules:

http.server, socket, socketserver, webbrowser, pyqrcode, png, and os.
Setting the port:

The server will run on port 8010.
Changing the working directory:

The directory is changed to the user's desktop to share files from there.
Creating an HTTP request handler:

SimpleHTTPRequestHandler from http.server is used.
Finding the host and IP address:

The hostname and IP address of the system are determined.
Generating the QR code:

The server's URL is converted into a QR code and saved as an SVG file.
Opening the QR code:

The generated QR code SVG is opened in the default web browser.
Starting the HTTP server:

The server is started and listens for incoming requests, allowing continuous file sharing.

Notes
Ensure your device is connected to the same network as the devices you want to share files with.
The port number (8010) can be changed if needed, but ensure the new port is open and not in use by other applications.

Troubleshooting
If the QR code does not open automatically, manually open the myqr.svg file located on the desktop.
If the server fails to start, check if the specified port is already in use or try a different port.
