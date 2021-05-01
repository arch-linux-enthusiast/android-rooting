## Welcome to the noobs guide to android rooting!!
In this page you will find the overview of android rooting. Though it changes from phone to phone, some steps remain the same.

# 1. Unlocking the bootloader

1. Enable developer options in your phone. This step varies from device to device. It should consist of clicking on build number, kernel version etc. from the phone settings > status.
2. Enable USB debugging from developer options
3. In some phones you might have to request bootloader unlock access. This will vary from device to device.
4. In other phones there should be an option of unlocking the bootloader and unlocking the oem bootloader right in the developer options.
5. Now that your bootloader is unlocked you should be able to access it by turning off your device and turning it back on while pressing the volume down/up button (you might have to experiment a little with this).

# 2. Installing the required tools on your PC

1. You will need the adb tools for rooting.
2. It is easiest to root if you are using Linux with proprietary drivers because you won't have a single issue with drivers. You will need adb as well as fastboot. The package names vary across distributions but here are a few:


    1. Arch Linux/other Arch based distros: android-tools (includes both)
    2. Ubuntu/Debian/Linux Mint/other Debian based distros: adb fastboot
    3. Fedora/SUSE: android-tools (with yum)
    4. If you use other distros which don't have adb and fastboot in the repos, you should [download the required tools](https://dl.google.com/android/repository/platform-tools-latest-linux.zip), cd into the respective directory and run the commands with "./" prefixing it.
3. If you are on Windows, the process isn't too complicated either. [This article gives an excellent explanation](https://www.stechguide.com/how-to-install-adb-and-fastboot-on-windows/). Just follow it step by step and you have what you need.

# 3. Making your android device trust your PC's RSA fingerprint
1. Connect your android device to your phone with a data cable, set the USB option in your phone to "file transfer" or "MTP" and then run "adb devices" in your PC from the command line (henceforth referred to as the terminal). This will work if you have installed the previous tools system-wide. If you have only downloaded them, see the next step.
2. If you get some error then move into the directory where the tools are downloaded and run "./adb devices". In Windows you might have to run ".\adb devices". Notice the difference which is subtle, in Windows you need to run it with a backslash (\).
3. Your phone should give a message about trusting RSA fingerprint of device. Select the "Always allow from this computer" and select OK. Your device should show up in the terminal window.
4. Note that this step is extremely crucial. Without your phone trusting the RSA fingerprint of your PC, you cannot root. Do not skip thinking it is a "testing" step of some kind.

# 4. Tools necessary in your android device
These tools are to be downloaded on your PC and later transferred when necessary to your phone.
1. Custom Recovery
    1. [TWRP](https://twrp.me/Devices) The exact link will vary from device to device, check if your device is available in the list
    2. [Orange Fox Recovery](https://orangefox.download/) Choose this if TWRP does not work, this is an alternative only. **You only need** *one* **of these two recoveries not both.**
2. [Magisk](https://magisk.me/zip/)
3. custom ROM (optional)

# 5. Flashing TWRP and booting into TWRP
Commands in quote blocks are to be run in the terminal.

> adb reboot bootloader

Your phone will now have rebooted into some sort of blank screen with fastboot mode or something similar written on it. The important thing to note is that the phone won't boot into system.

Check if fastboot recognisese your device. This needs to be run with elevated privileges so first run "su" if on Linux or run these from an administrator cmd.

> fastboot devices

If your device is recognised, go ahead. If not google with the code name for your device.

Change directory to where you have downloaded the [Custom Recovery](1-custom-recovery)

> fastboot flash recovery <exact name of the recovery file>.img

> fastboot boot recovery <exact name of the recovery file>.img
 
# 6. Flashing Magisk if you do not want to remove stock ROM which is provided with phone. Skip this step for now if you want to install Custom ROM.
After the last step shown above, you should now be in TWRP/OrangeFOx recovery. Connect your phone to your laptop now.

Both the recoveries start MTP on being booted into so your PC should pick them up and you should be able to browse them with your file manager. 

However I was having trouble browsing in Arch Linux because my file manager wasn't able to detect the MTP devices. I solved this problem by installing gvfs-mtp package which took care of the problem completely

Now you should move into the directory where you downloaded the Magisk ZIP on your PC and copy the file over to your phone, preferably in the home directory so that it is easy to find when installing it.

Now disconnect your phone from PC and install the Magisk ZIP by selecting Install. It is quite easy and you can figure out the exact steps by yourself since it is all a pretty GUI anyway.

Then you should Wipe Cache/Dalvik before rebooting into your system. The first time you do reboot might take some time.

