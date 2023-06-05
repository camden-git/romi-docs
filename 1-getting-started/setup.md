# Chapter 1 - Setup the Romi

## Prerequisites

Before you begin, make sure you have the following:

- Assembled Romi with charged batteries
- Laptop running Windows, Mac, or Linux
- WPILib VSC 2022 installed either via the [installer](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html) or the [VSC extension](https://marketplace.visualstudio.com/items?itemName=wpilibsuite.vscode-wpilib)
- If you want to prepare in advance, you can install [Balena Etcher](https://www.balena.io/etcher/) and download [the latest Romi firmware image](https://github.com/wpilibsuite/WPILibPi/releases). Make sure to download [the correct file](https://docs.wpilib.org/en/stable/_images/romi-download.webp).
- *Optional* Ensure you have a microSD card reader or an appropriate device, as there might not be enough in the lab.

## Flashing your Romi

## Raspberry Pi

The Romi utilizes a Raspberry Pi for high-level communication with the robot program running on your desktop. Follow the steps below to install the necessary firmware:

*If you need any assistance or have questions, don't hesitate to reach out to a leader or another team member.*

<img align="right" src="hhttps://raw.githubusercontent.com/camden-git/romi-docs/main/assets/romi-download.webp" width="350">

1. Download the Romi version of WPILibPi from the [GitHub Romi Release](https://github.com/wpilibsuite/WPILibPi/releases) page. Make sure to choose the Romi version and not the standard release.  

2. Once downloaded, write the firmware to the micro SD card of your Raspberry Pi using a tool like [Balena Etcher](https://www.balena.io/etcher/). This process is described in detail in the [WPILibPi Installation](https://docs.wpilib.org/en/stable/docs/software/vision-processing/wpilibpi/installing-the-image-to-your-microsd-card.html) guide.

3. After completing the firmware flashing process, you can locate the boot partition of the micro SD card in your file explorer (such as Explorer, Finder, or the Linux DE equivalent). Look for a drive labeled "boot" or "pi"

4. Once you've located this, open the folder called `boot` and you will find a file named "default-ssid.txt." Open this file using a text editor and modify it to set your desired Wi-Fi network name (SSID) and password. You can write down this information on a piece of tape and securely attach it to the battery compartment, which is located on the underbelly of the Romi.

5. Remember to save the changes to the "default-ssid.txt" file after editing it. This will ensure that your Romi connects to the Wi-Fi network with your specified credentials.

6. After writing the firmware and setting your WiFi settings, turn on the Romi by sliding the power switch on the Romi 32U4 board to the on position. The first boot may take a few minutes to resize the file system and reboot.

7. Connect your computer to the Romi WiFi network using the SSID & password you set before.

8. Open a web browser and navigate to either `http://10.0.0.2/` or `http://wpilibpi.local/` to access the Raspberry Pi dashboard.

**Congratulations! If you see a webpage load, you have successfully set up your Romi!**

*If you need any assistance or have questions, don't hesitate to reach out to a leader or another member.*

## Romi 32U4 Control Board

**If you have just flashed your Raspberry Pi with the Romi firmware, you can skip this step.**  

**Caution: If you have not performed this procedure before, it is strongly recommended to seek assistance from a senior member or experienced individual. Improper execution of this process can permanently DESTROY your Romi.**  
If you encounter any issues with your Romi 32U4 Control Board or if it is out of date, you can easily flash the firmware using the webUI. Follow these steps:

1. Turn off the Romi.

2. Connect a USB A to micro-B cable from one of the Raspberry Pi's USB ports to the micro USB port on the 32U4 Control Board.

3. Turn on the Romi and connect to its WiFi network. Access the web dashboard using the same steps as before.

4. On the Romi configuration page, locate and press the **Update Firmware** button.

5. A console will appear, showing a log of the firmware deployment process. Once the firmware has been successfully deployed to the 32U4 Control Board, you will see the message "avrdude done. Thank you.".

Congratulations! You have successfully imaged your Romi with the necessary firmware for operation.

*Images credit: <https://docs.wpilib.org/en/stable/docs/romi-robot/imaging-romi.html>*  

[Back - Basics](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/basics.md) | [Home](https://github.com/camden-git/romi-docs/) | [Chapter Home](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/intro.md)
