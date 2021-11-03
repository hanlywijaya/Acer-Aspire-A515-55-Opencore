# Acer-Aspire-A515-55-Opencore
Opencore EFI for Acer Aspire 5 (A515-55). Intended for Ice Lake systems, may work on other types of CPU families but not guaranteed to work and function as intended.

### **I am not responsible for any damage or if your computer turns into a lemon all of a sudden. Everything you do is not guaranteed to work & you are responsible.**
### **PLEASE READ THE WHOLE README FILE TO UNDERSTAND WHAT TO DO FOR THIS EFI.**

### Supports macOS Big Sur and macOS Monterey (can be installed now!)

### FAQ:

Q: Why did you upload an EFI of Opencore for the A515-55?
A: I found that many people haven't hackintoshed the A515-55 and I wanted to try it. I also wanted to upload it for people to try and use it for hackintoshing their systems.

Q: What OS do you recommend for fixing up things for this EFI?
A: I do recommend having an existing macOS installation to edit bits and pieces of the EFI. Things needed to change by you will be below.

Q: What version of Opencore and model of Aspire A515-55 is recommended for this?
A: The version of Opencore used on the Aspire A515-55 is 0.7.5 (latest as of 3 November 2021) & the model of A515-55 that I recommend using is an Intel Ice Lake model of the Aspire 5.

Q: Can I use this on other models of Acers? (Aspire 3, Swift, etc)
A: There is a chance it will work but it is not guaranteed to work properly due to this EFI being specifically built for Acer Aspire A515-55.

Q: Will I need to map anything on macOS?
A: I recommend changing the option key to command then changing command to option in the keyboard pane located in System Preferences.

Q: What is the recommended version of macOS with this EFI?
A: I recommend using macOS Big Sur as it is very reliable and easy to do. For Big Sur, make sure you use 0.7.4-3-BS. If you would like to use Monterey, use the latest EFI and make sure all your apps will work.

Q: Do I need to change anything in the config.plist file?
A: You will need to change the model number along with the serial number. You can keep the model number but I do recommend following the Opencore guide linked in this answer. The link is below in what is needed to be changed. (https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios)

Q: Why do I need to change the key and model number?
A: You will need it for booting into macOS and having working iCloud, iMessage and FaceTime functionality to work no problem and spoof Apple into thinking your computer is an Apple computer.

Q: What is the recommended CPU family for everything to be reliable and working?
A: I recommend Ice Lake CPUs (i7-1065G7 for example) for the best reliability since this EFI is built off the Ice Lake architecture. Tiger Lake (11th gen Intel CPUs) will not work with this EFI and there is a chance that older CPU families from before Ice Lake may work but may have issues and are not on me.

Q: Sometimes sleep doesn't work, what can I do?
A: I recommend trying to use 'lock screen' in the Apple menu then click cancel then it should turn off the screen. You should be able to just close the lid.

Q: My battery drains quick. What can I do
A: That is normal for Acer laptop hackintoshes. I have not found a way to make the battery use more efficient.

Q: Can I install macOS Monterey with this EFI?
A: This EFI is optimized for Big Sur and you will need to modify many things with this EFI, including changing kexts and fixing your plist file. I recommend sticking with Big Sur for now and I may update this EFI for macOS Monterey when it is released or when it has been updated to 12.0.1/12.1

Q: When I login, the screen goes black for a few seconds. What can I do?
A: Since its a Ice Lake Intel system, this cannot be fixed at the moment. Its normal due to the Intel GPU (iGPU) not working properly with macOS.

### Important
 Please add `SystemSerialNumber`, `SystemUUID` and `MLB`, along with updating some BIOS settings listed below.

I recommend if you are using a different type of CPU model, to follow the Opencore guide on fixing up the configuration plist to be built for your Mac. You may want to use my EFI as an template for everything you need. - https://dortania.github.io/OpenCore-Install-Guide/

### BIOS Settings
* *Security* → Set supervisor password (to disable secure boot)
* *Security* → Password on boot → **Disable**
* *Boot* → Secure Boot → **Disable**
* *Boot* → Boot Mode → **UEFI**
* *Main* → Lid Open resume → **Enabled**

### Tested

- [x] Dual booting functionality (Windows & macOS)
- [x] Internal Audio and Headphone Jack
- [x] iGPU Acceleration
- [x] Battery Readings
- [x] Ethernet
- [x] Wifi + Bluetooth
- [x] Display Brightness Control (partially working with 0.7.5)
- [ ] Sleep Functionality (you can use lid open and sleep as a alternative)
- [x] Lid Close and Open (semi-working)
- [x] USB ports (3.0, 2.0 & USB-C)
- [x] Webcam
- [x] Trackpad with multi finger gestures 
- [ ] HDMI (you can use AirPlay/USB-C to HDMI as a alternative)
- [x] Native hotkey support with Fn keys

### Specs for tested Aspire 5:
1.30ghz Intel Core i7-1065G7 (Ice Lake)
8GB RAM
Intel Iris Plus Graphics 1536MB (iGPU)
Realtek ALC255 (using layout 30 for AppleALC)

### SMBIOS used for my model (recommended to follow guide link in **What is needed to be changed**)
MacBookPro16,2 (13-inch, 2020, Four Thunderbolt 3 ports)

### How to fix IntelBluetooth on 0.7.4-3-M to 0.7.5
Good news! Intel Bluetooth has gotten a fix on Monterey and now functions as intended. I will be sending out 0.7.5-M when 0.7.5-stock is ready from Acidanthera. If you would like to fix yours up, I recommend using MacBookPro16,2 SMBIOS (for Ice Lake). You have to use the latest commit, **not release** from github.com/dortania/build-repo & make sure that IntelBluetoothInjector is removed/disabled from config.plist. Reset the NVRAM through the Opencore Boot Picker then you are all set!

### BIOS Settings
* *Security* → Set supervisor password (to disable secure boot)
* *Security* → Password on boot → **Disable**
* *Boot* → Secure Boot → **Disable**
* *Boot* → Boot Mode → **UEFI**
* *Main* → Lid Open resume → **Enabled**

### Guide
This guide will help you from the start to the end : [Dortania Gitbook](https://dortania.github.io/OpenCore-Install-Guide/)
Generating Serial Number : GenSMBIOS from Corpnewt [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)

### How to install/upgrade EFI
For installing macOS, put the EFI in the EFI partition. To mount the EFI partition, go to Terminal, and type 'diskutil list'. It should show a list of disks and one of the disks should be the installer (should have the same name as the USB you will be using for installing' and a partition in the list with the installer named 'EFI'. Do not choose disk0s1 (main disk) or disk1s1 (if you have a second disk installed) and find for example, disk2s1. There should be a identifier for example, 'disk3s1'. You want to type 'sudo diskutil mount diskidentifier' then type your password to mount the EFI. After proceeding, you will need to change your model idenifier, serial number, ROM & MLB for iCloud, iMessage & FaceTime to function, along with being able to install and boot macOS. You can place a copy of the latest EFI from the GitHub repo and make sure you have replaced the wordings for model identifier, serial number & ROM have been replaced. I recommend using Opencore Configurator as it is easy to use for most users. Go to PlatformInfo and the first tab in Opencore Configurator and replace all the placeholder texts, I recommend using the guide for easier instructions. (https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios) 

For upgrading your EFI, you simply only need to follow all the steps and use the same serial number, model identifier, etc in the config.plist file for the newest EFI. Do not replace your SMBIOS (serial number, model identifier, etc) if you are still logged into iCloud. If you want to change your SMBIOS, you will need to log out of iCloud & other Apple services to be able to swap your SMBIOS without issues.


###  Basic Installation

- Create a Bootable USB for MacOS by using by Dortania's [OpenCore-Install-Guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/).
- Install MacOS to SSD / Hard drive. (While installing, connect USB keyboard and mouse).
- Copy **ALL** the Contains of this Repo inside the EFI partition of SSD / Hard drive.
- **[IMPORTANT]** Make sure to Generate system definitions of MacBookPro16,2 (for those who use 10th gen Intel/Ice Lake) in config.plist file using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) & add `SystemSerialNumber`, `SystemUUID` and `MLB`.

### Post Installation
- If you have Installed MacOS on SSD, Enable TRIM using following command:

```sh

$ sudo trimforce enable

```

### The transition from Big Sur to Monterey
Monterey requires different drivers and kexts meaning, that you have to use 0.7.4-3-M or newer to install and use Monterey. The best way of an easy transition is following the steps on how to install/upgrade to Monterey. The new EFI is released. Many things may be problems and as we get more Monterey updates, the more that gets fixed. 0.7.4-3-M is built for Monterey which also supports the RC version (12.0.1). Only thing not functioning properly is IntelBluetooth in 0.7.4-3-M. 0.7.5-M will resolve that issue and will be able to be used no problem. More info on that on https://github.com/hanlywijaya/Acer-Aspire-A515-55-Opencore/issues/2. It may take up to 6 months for a proper transition. If Bluetooth is cruical to you, lucky news! You can get 0.7.5 now & will be able to have perfectly functioning IntelBluetooth! Monterey is now available to update.

### How to update

-- If you are simply updating for example (11.6 to 11.6.1), you can simply update it like any Mac.

-- If you are updating to a new OS for example (Big Sur to Monterey), you need to follow the steps below.
1. Download the OS installer. You can get one from the App Store.
2. Get a 16GB USB/partition and format it as a Extended Journal & not APFS. Make sure it is a GUID Table too.
3. Back up your computer with Time Machine or copy your files to iCloud/USB/SSD to keep it safe. (Optional)
4. Download the latest EFI for the OS you need in the releases page of this repository.
5. Install the EFI **on the USB/partition** and do the needed steps. **DO NOT INSTALL THE EFI ON YOUR EXISTING MACOS PARTITION OTHERWISE YOU MAY NOT BE ABLE TO BOOT INTO THE OS ALREADY INSTALLED ON YOUR DISK (SSD/HDD)** (steps somewhere above in this README)
6. Use createinstallmedia of your installer onto your USB. You will need a Mac and instructions are on https://support.apple.com/en-us/HT201372.
7. Boot into the external USB EFI and boot into your installer.
8. **(Optional)** You can boot into your BIOS and make your USB the first boot selection.
9. Install macOS like normal. **DO NOT ERASE YOUR DISK UNLESS YOU WOULD LIKE A FRESH INSTALL INSTEAD OF A KEEP ALL FILES IN SAME STATE UPGRADE.** Make sure that when your computer reboots while installing, that you boot into your USB's EFI and boot into 'macOS Installer'.
10. When your computer doesn't show 'macOS Installer' and instead shows your disk's name, that means that your installation is complete.
11. Boot into your install through the USB and continue setup like normal. If you wiped your computer to have a fresh install, you can either set it up as a new Mac or restore a Time Machine backup or simply migrate using the Migration Assistant later.
12. You will need to copy your USB's EFI to your computer. Simply follow the steps above in the README and instead of getting a fresh copy of the latest EFI for your OS from the repository, simply copy the EFI from your USB and use that, unless the EFI is acting funny.
13. Congrats! You're done!

### Development and Functionality
If you would like to help/add items to give extra functionality to Aspire A515-55, you can make an issue with the tag 'feature enhancement'.


<p align="center">
<b>⭐ Please consider starring this repository if it helped you! ⭐</b>
</p>
