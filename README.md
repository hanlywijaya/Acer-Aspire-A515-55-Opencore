# Acer-Aspire-A515-55-Opencore
Opencore EFI for Acer Aspire 5 (A515-55).

**I am not responsible for any damage or if your computer turns into a lemon all of a sudden. Everything you do is not guaranteed to work & you are responsible.**
**PLEASE READ THE WHOLE README FILE TO UNDERSTAND WHAT TO DO FOR THIS EFI.**


FAQ:

Q: Why did you upload an EFI of Opencore for the A515-55?
A: I found that many people haven't hackintoshed the A515-55 and I wanted to try it. I also wanted to upload it for people to try and use it to see if they can work with it.

Q: What OS do you recommend for fixing up things for this EFI?
A: I do recommend having an existing macOS installation to edit bits and pieces of these. Things needed to change by you will be below.

Q: What version of Opencore and model of Aspire A515-55 is recommended for this?
A: The version of Opencore used on the Aspire A515-55 is 0.7.2 (latest as of 25 aug 2021) & the model of A515-55 that I recommend using is an Intel Ice lake model of the Aspire 5.

Q: Can I use this on other models of Acers? (Aspire 3, Swift, etc)
A: There is a chance it will work but it is not guaranteed to work properly due to this EFI being specifically built for Acer Aspire A515-55.

Q: Will I need to map anything on macOS?
A: I recommend changing option to command and command to option. You can keep it the way it is if you like. You change the mapping from the keyboard preferences in System Preferences.

Q: What is the recommended version of macOS with this EFI?
A: I recommend Big Sur for the best stability and stay on it. When Monterey releases, I will try to update my EFI for it to work perfectly on Monterey.

Q: Do I need to change anything in the config.plist file?
A: You will need to change the model number along with the serial number. You can keep the model number but I do recommend following the Opencore guide linked in this answer. The link is below in what is needed to be changed.

Q: Why do I need to change the key and model number?
A: You will need it for booting into macOS and having working iCloud, iMessage and FaceTime functionality to work no problem and spoof Apple into thinking your computer is an Apple computer.

What is needed to be changed?
You will need to change the model number/serial number/etc to fix iCloud and etc. - https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios

I recommend if you are using a different type of CPU model, to follow the Opencore guide on fixing up the config to be built for your Mac. You may want to use my EFI as an template for everything you need. - https://dortania.github.io/OpenCore-Install-Guide/

Tested/Untested

Speakers : Tested
Headphone jack : Untested
Internal keyboard : Tested
Touchpad : tested
Usb ports + USB-C port : tested
Sleep : partially working with a macOS specific fix
HD Camera : tested
Brightness & sound change : tested
Specific Acer features : disable screen + backlight, enable or disable backlight, disable touchpad, have been tested and works perfectly.
iCloud, FaceTime & iMessage : tested

Specs for tested Aspire 5:
1.30ghz Intel Core i7-1065G7 (Ice Lake)
8GB RAM
Intel Iris Plus Graphics 1536MB

SMBIOS used for my model (recommended to follow guide link in **What is needed to be changed**)
MacBookAir9,1 (MacBook Air, Retina, 13 inch, 2020)
