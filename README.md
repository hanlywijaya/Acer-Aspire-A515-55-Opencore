# Acer-Aspire-A515-55-Opencore
Opencore EFI for Acer Aspire 5 (A515-55).

**I am not responsible for any damage or if your computer turns into a lemon all of a sudden. Everything you do is not guaranteed to work & you are responsible.**
**PLEASE READ THE WHOLE README FILE TO UNDERSTAND WHAT TO DO FOR THIS EFI.**


FAQ:

Q: Why did you upload an EFI of Opencore for the A515-55?
A: I found that many people haven't hackintoshed the A515-55 and I wanted to try it. I also wanted to upload it for people to try and use it for hackintoshing their systems.

Q: What OS do you recommend for fixing up things for this EFI?
A: I do recommend having an existing macOS installation to edit bits and pieces of the EFI. Things needed to change by you will be below.

Q: What version of Opencore and model of Aspire A515-55 is recommended for this?
A: The version of Opencore used on the Aspire A515-55 is 0.7.3 (latest as of 8 sep 2021) & the model of A515-55 that I recommend using is an Intel Ice lake model of the Aspire 5.

Q: Can I use this on other models of Acers? (Aspire 3, Swift, etc)
A: There is a chance it will work but it is not guaranteed to work properly due to this EFI being specifically built for Acer Aspire A515-55.

Q: Will I need to map anything on macOS?
A: I recommend changing the option key to command then changing command to option in the keyboard pane located in System Preferences.

Q: What is the recommended version of macOS with this EFI?
A: I recommend using macOS Big Sur 11.5.1 (the latest of the time) as it is very reliable and easy to do.
Q: Do I need to change anything in the config.plist file?
A: You will need to change the model number along with the serial number. You can keep the model number but I do recommend following the Opencore guide linked in this answer. The link is below in what is needed to be changed.

Q: Why do I need to change the key and model number?
A: You will need it for booting into macOS and having working iCloud, iMessage and FaceTime functionality to work no problem and spoof Apple into thinking your computer is an Apple computer.

Q: Sometimes sleep doesn't work, what can I do?
A: I recommend trying to use 'lock screen' in the Apple menu then click cancel then it should turn off the screen. You should be able to just close the lid.

Q: My battery drains quick. What can I do?
A: That is normal for Acer laptop hackintoshes. I have not found a way to make the battery use more efficient.

Q: Can I install macOS Monterey with this EFI?
A: This EFI is optimized for Big Sur and you will need to modify many things with this EFI, including changing kexts and fixing your plist file. I recommend sticking with Big Sur for now and I may update this EFI for macOS Monterey when it is released or when it has been updated to 12.0.1/12.1

Q: When I login, the screen goes black for a few seconds. What can I do?
A: Since its a Ice Lake Intel system, this cannot be fixed at the moment. Its normal due to the Intel GPU (iGPU) not working properly with macOS.

Q: What happened to the boot GUI from 0.7.2 & 0.7.2-2 on 0.7.3?
A: The GUI has not been working since 0.7.3. I will not be sending out a solution just yet and will update when I get the GUI fixed. For now, it wil be a text GUI. You can stay on 0.7.2-2 if you want the GUI but it will not be the latest and greatest.

What is needed to be changed?
You will need to change the model number/serial number/etc to fix iCloud and etc. - https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios. You will also need to change a few things in the BIOS. To boot into the BIOS, turn on the computer, press & hold F2 (function key row) until it shows a blue screen with some text (may show a password, type the password set for the BIOS if needed). You will need to go to the 2nd tab of the BIOS by pressing the right arrow key and press Ctrl+S (no + btw). You will need to change the disk type from Optane to AHCI & make sure that the touchpad is in I2C mode. I recommend also enabling the F12 boot menu so you can easily change boot disks (Opencore EFI to Windows partition, etc) & go to the 2nd last tab then setting a password then disabling Secure boot. You will need to disable Secure boot since this is not an EFI that supports Secure boot. You will also need to type your password whenever you need to boot into the BIOS so make sure you remember the password. You can go to the last tab and save & exit.

I recommend if you are using a different type of CPU model, to follow the Opencore guide on fixing up the configuration plist to be built for your Mac. You may want to use my EFI as an template for everything you need. - https://dortania.github.io/OpenCore-Install-Guide/

Tested/Untested

Speakers & Microphone : works
Headphone jack : works
Internal keyboard : works
Touchpad : worked (must be in I2C mode)
Usb ports + USB-C port : works
Sleep : partially working with a macOS specific fix
HD Camera : works
Brightness & sound change : works
Specific Acer features : function keys (brightness, backlight, turn off display, sleep, etc) works (project doesn't work with macOS, use airplay)
iCloud, FaceTime & iMessage : works (must have a invalid serial number / serial number that is not validated)

Specs for tested Aspire 5:
1.30ghz Intel Core i7-1065G7 (Ice Lake)
8GB RAM
Intel Iris Plus Graphics 1536MB (iGPU)
Realtek ALC255 (using layout 30 for AppleALC)

SMBIOS used for my model (recommended to follow guide link in **What is needed to be changed**)
MacBookAir9,1 (MacBook Air, Retina, 13 inch, 2020)
