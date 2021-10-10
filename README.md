# Acer-Aspire-A515-55-Opencore
Opencore EFI for Acer Aspire 5 (A515-55).

### **I am not responsible for any damage or if your computer turns into a lemon all of a sudden. Everything you do is not guaranteed to work & you are responsible.**
### **PLEASE READ THE WHOLE README FILE TO UNDERSTAND WHAT TO DO FOR THIS EFI.**

### Supports macOS Big Sur 11.6

### FAQ:

Q: Why did you upload an EFI of Opencore for the A515-55?
A: I found that many people haven't hackintoshed the A515-55 and I wanted to try it. I also wanted to upload it for people to try and use it for hackintoshing their systems.

Q: What OS do you recommend for fixing up things for this EFI?
A: I do recommend having an existing macOS installation to edit bits and pieces of the EFI. Things needed to change by you will be below.

Q: What version of Opencore and model of Aspire A515-55 is recommended for this?
A: The version of Opencore used on the Aspire A515-55 is 0.7.4 (latest as of 8 October 2021) & the model of A515-55 that I recommend using is an Intel Ice Lake model of the Aspire 5.

Q: Can I use this on other models of Acers? (Aspire 3, Swift, etc)
A: There is a chance it will work but it is not guaranteed to work properly due to this EFI being specifically built for Acer Aspire A515-55.

Q: Will I need to map anything on macOS?
A: I recommend changing the option key to command then changing command to option in the keyboard pane located in System Preferences.

Q: What is the recommended version of macOS with this EFI?
A: I recommend using macOS Big Sur 11.6 (the latest of the time) as it is very reliable and easy to do.

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
- [x] Display Brightness Control (partially working with 0.7.4)
- [ ] Sleep Functionality
- [x] USB ports (3.0, 2.0 & USB-C)
- [x] Webcam
- [x] Trackpad with multi finger gestures 
- [ ] HDMI
- [x] Native hotkey support with Fn keys

### Specs for tested Aspire 5:
1.30ghz Intel Core i7-1065G7 (Ice Lake)
8GB RAM
Intel Iris Plus Graphics 1536MB (iGPU)
Realtek ALC255 (using layout 30 for AppleALC)

SMBIOS used for my model (recommended to follow guide link in **What is needed to be changed**)
MacBookAir9,1 (MacBook Air, Retina, 13 inch, 2020)

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
- **[IMPORTANT]** Make sure to Generate system definitions of MacBook pro 15,4 in config.plist file using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) & add `SystemSerialNumber`, `SystemUUID` and `MLB`.

### Post Installation
- If you have Installed MacOS on SSD, Enable TRIM using following command:

```sh

$ sudo trimforce enable

```

### Development and Functionality
If you would like to help/add items to give extra functionality to Aspire A515-55, you can make an issue with the tag 'feature enhancement'.


<p align="center">
<b>⭐ Please consider starring this repository if it helped you! ⭐</b>
</p>
