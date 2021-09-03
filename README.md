# PZEM-016 - Serial-Modbus
## Energy Monitor - PZEM-016 - Nodered
The purpose of this repository is to memorialize the base configuration of nodered on a Raspberry Pi 4B - 8GB. Using the an offical image for "Raspberry Pi OS with desktop and recommended software" that can be downloaded from:

https://www.raspberrypi.org/software/operating-systems/#raspberry-pi-os-32-bit

  - Nodered is istalled as part of the above named quoted referenced image. Nodered should be configured to automatically startup at boot on the Pi and that must be done manually. I typicall do this step through a VNC connection to the Pi and then at a terminal propmt issuing the following shell commands:
    - sudo systemctl enable nodered.service
    - sudo systemctl start nodered.service

On either the Pi or a desktop computer open the web interface to nodered typically located as follows:
  - On the Pi
    - http://127.0.0.1:1880
  - On a remote computer (same LAN)
    - http://192.168.1.219:1880 (replacing the ip address to however your lan is configured)

Two nodered dependency palettes must be installed:
  - node-red-contrib-modbus
    - Faciliates communication of a flow (serial, tcp, etc)
  - node-red-dashboard
    - Assorted UI (user interface) controls

Installing the required palettes is straight forward and can be done through the web as linked above. You first go to the vertical stack menue and choose Manage Palette. Then select the install tab. Coping and pasting the name of the package and clicking the magnifing glass icon or pressing enter will bring the package up in the list. Click the install button.
![GitHub Logo](/images/Nodered-Manage-Palette.jpeg)
Format: ![Alt Text](url)

