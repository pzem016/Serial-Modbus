# PZEM-016 - Serial-Modbus
## Energy Monitor - PZEM-016 – Node-Red
The purpose of this repository is to memorialize the base configuration of Node-Red on a Raspberry Pi 4B - 8GB, manage the PZEM-016 device through a RS485 serial modbus and create an informative and useful user interface. Please note that Node-Red is available for various platforms however this repository discusses the Pi as the hardware and software platform. It is expected that this configuration should work on other operating system however is untested. Using the official image titled "Raspberry Pi OS with desktop and recommended software" can be freely downloaded from:

- https://www.raspberrypi.org/software/operating-systems/#raspberry-pi-os-32-bit

There are some excelent photos of the PZEM-016 available here:
- https://community.openenergymonitor.org/t/pzem-016-single-phase-modbus-energy-meter/7780/22
- https://community.openenergymonitor.org/t/pzem-016-single-phase-modbus-energy-meter/7780/35

Node-Red is installed as part of the above named quoted referenced image. Node-Red must be configured to automatically startup at boot on the Pi and that is accomplished manually. In keeping this as a visual tutorial, a typical workflow is through a VNC connection to the Pi and then at a (scarcely used) terminal prompt issuing the following two shell commands:
  - sudo systemctl enable nodered.service
  - sudo systemctl start nodered.service
  - Chained together for a single cut and paste: 
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

Now that the dependencies are met, the following will detail the process of integrating the RS482 to USB on the Pi.


## Design Considerations

- Establish a consistent serial connection for devvice(s) polling
  - Utilize the Modbus Flex series of controls
  - Configuration of the numbered /dev/ttyUSB[0] 
    - The Pi has four native USB ports
    - Select a USB 2 for the communications
    - Shell command:
      - sudo ls -la /dev/ttyUSB*
  - /dev/ttyUSB0 will be used throughout the remainder of this guid
  - Configure the Modbus serial interface
  - Drop in a Modbus Flex Getter object on to a flow
    - Create/Edit the server
![GitHub Logo](/images/Modbus-Flex-Getter.png)![GitHub Logo](/images/Modbus-Client-Config.png)
