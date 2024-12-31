# Basic Hello World for ESP-IDF blink on ESP32-C6 (Board: ESP32-C6-DevkitM-1)

This repo is for ESP-IDF with PlatformIO, and is a fork of the repo from @Graunephar (www.github.com/Graunephar). I modified it to build in a devcontainer for the ESP32C6-devkitM-1 board. 
Usage: Requires Windows 11 with WSL2, Docker Desktop and VsCode Installed.
Clone the repo from VsCode using "Dec Containers: Clone Repository in Container Volume..." 
Once the Container has booted up, follow the recommendation to install the PlatformIO (PIO) extension into the Ubuntu container.
Run the PIO extension and this should install PIO core into the Ubuntu container.
Build the code in PIO (Use tool at the bottom of screen or run "PIO run" from a terminal).
Before you can upload you need to connect the usb port to the Ubuntu container.

From the PIO terminal, run the shell script in the .decontainer directory called setusbport.sh, with the following:

bash setusbport.sh

This should create the link to the /dev/ttyUSB0 device

Plug in the ESP32C6 DevkitM board into the USB port
and run the following commands from a Command Prompt window in WINDOWS running as Administrator:

usbipd list    (to see the BUSID)

usbipd bind BUSID

usbipd list    (should show BUSID as SHARED)

usbipd attach --wsl --busid BUSID (you should hear the connect sound)

Return to VsCode and from a PIO New Terminal type: "pio device list" 
and see something like this:

vscode ➜ /workspaces/ESP32-C6-LED-blink-ESP-IDF-PlO-DevC (main) $ pio device list
/dev/ttyUSB0
------------
Hardware ID: USB VID:PID=10C4:EA60 SER=a4029672ef1aef11970a13764909ffd0 LOCATION=1-1
Description: CP2102N USB to UART Bridge Controller

Upload the code from the bottom tool bar, or type from the PIO terminal:
pio run -t upload






 

