# PZEM-016 - Serial-Modbus
## Energy Monitor - PZEM-016 – Node-Red
The purpose of this repository is to memorialize the base configuration of Node-Red on a Raspberry Pi 4B - 8GB, manage the PZEM-016 device through a RS485 serial modbus and create an informative and useful user interface. Using the official image titled "Raspberry Pi OS with desktop and recommended software" can be freely downloaded from:

https://www.raspberrypi.org/software/operating-systems/#raspberry-pi-os-32-bit

  - Node-Red is installed as part of the above named quoted referenced image. Node-Red must be configured to automatically startup at boot on the Pi and that is accomplished manually. In keeping this as a visual tutorial, a typical workflow is through a VNC connection to the Pi and then at a terminal prompt issuing the following two shell commands:
  - sudo systemctl enable nodered.service
  - sudo systemctl start nodered.service
  - Chained for one cut and paste: 
    - sudo systemctl enable nodered.service && sudo systemctl start nodered.service

On either the Pi or a desktop computer open the web interface to Node-Red typically located as follows:
  - On the Pi
    - http://127.0.0.1:1880
  - On a remote computer (same LAN as the Pi)
    - http://192.168.1.219:1880 (replacing the ip address to however your lan is configured)

Two Node-Red dependency palettes must be installed:
  - node-red-contrib-modbus
    - Facilitates communication of a flow (serial, tcp, etc)
  - node-red-dashboard
    - Assorted UI (user interface) controls

Installing the required palettes is straight forward and can be completed through the web interface linked above. You first go to the vertical stack menu and choose Manage palette. On the User Settings dialog, select the install tab. Coping and pasting the name of the above dependency package and pressing enter will present the most recent package in the list. Finally, click the install button. Repeat the search and install process until both are installed.

![GitHub Logo](/images/Nodered-Manage-Palette.png)
![GitHub Logo](/images/Nodered-Search-Palette1.png)
![GitHub Logo](/images/Nodered-Search-Palette2.png)


