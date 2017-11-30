# Configuration and setup information
* Get image and install
  * Debian 9.2 2017-10-10 Stretch non-GUI image used for this stuff
    * Image from here https://beagleboard.org/latest-images
  * Download and place image onto sd card with Etcher https://etcher.io/
    * info here https://beagleboard.org/getting-started#update
  * Place sd card into BBB sd card slot.
  * Plug usb cable into windows machine then hold User/Boot button on BBB and plug in usb cable to BBB.
  * Once BBB is powered up use putty to talk to BBB at this address via ssh http://192.168.7.2 username: debian password: temppwd
  * Use nano as per https://elinux.org/Beagleboard:BeagleBoneBlack_Debian#Flashing_eMMC  
    `sudo nano /boot/uEnv.txt`  
    Change this line
    ```   
    ##enable BBB: eMMC Flasher:`   
    #cmdline=init=/opt/scripts/tools/eMMC/init-eMMC-flasher-v3.sh
    ```
    To this line   
    ```
    ##enable BBB: eMMC Flasher:`   
    cmdline=init=/opt/scripts/tools/eMMC/init-eMMC-flasher-v3.sh
    ```
    * note the difference here is the # removed from second line.
  * Issue Reboot command from command line.
  * Device will reboot and the 4 leds will start to blink in a repeating pattern.
  * eMMC is programed when the 4 leds turn off solid or on solid and the power led turns off.
  * Now remove the SD card.
* Update Debian
  * Power back up with windows usb cable.  Plug in ethernet to router.
  * Issue these commands   https://elinux.org/Beagleboard:BeagleBoneBlack_Debian#Kernel_Upgrade
  ```
  sudo apt-get update
  cd /opt/scripts/tools/
  git pull
  sudo ./update_kernel.sh
  sudo reboot
  ```
