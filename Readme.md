# MacOS Catalina 
##              Ultrawide monitor 2560 x 1080 setup (LG U29UM59)

Do with your own risk , not responsible for any damage to your device.

If you do not want to deal with the hassle and the risk of messing up your system. SwitchResX is good tool for this.


## Reference:

Credits to all the people that figured out this hack in the links below . 

https://www.tonymacx86.com/threads/lg-ultrawide-29um57-p.179861/#post-1373704
https://www.tonymacx86.com/threads/adding-using-hidpi-custom-resolutions.133254/page-57
https://comsysto.github.io/Display-Override-PropertyList-File-Parser-and-Generator-with-HiDPI-Support-For-Scaled-Resolutions/


## Step:


### 1.Disable System Integrity Protection

     1. Reboot the Mac and hold down Command + R keys simultaneously after you hear the startup chime, this will boot Mac OS X into Recovery Mode
     2. When the “MacOS Utilities” / “OS X Utilities” screen appears, pull down the ‘Utilities’ menu at the top of the screen instead, and choose “Terminal”

     3.Type the following command into the terminal then hit return:

```
csrutil disable; reboot
```

Check status after reboot. You should see " System Integrity Protection status: disabled."

```
csrutil status
```

### 2. Enable HiDPI Mode
```
sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true
```

### 3. Detect your Display
```
ioreg -lw0 | grep IODisplayPrefsKey
```

Output:
```
"IODisplayPrefsKey" = "IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/IGPU@2/AppleIntelFramebuffer@0/display0/AppleBacklightDisplay-610-a019"
"IODisplayPrefsKey" = "IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/IGPU@2/AppleIntelFramebuffer@2/display0/AppleDisplay-1e6d-59f1"
```
AppleDisplay-1e6d-59f1 <-- LG29UM59 that we are looking to change.

Nothing needed to be done from this step if you can find "AppleDisplay-1e6d-59f1" from your output screen. Else , the setup below might not work for you.

### 4. Download DisplayProductID-59f1.plist in this repo.


### 5. Copy DisplayProductID-59f1 to /System/.. 

On Mac OS Catalina systems, the /System/ folder is mounted read-only, so you may need to temporarily remount the file system as writable before copying the downloaded file as follows: sudo mount -uw /.
```
sudo mount -uw /
```

Please back up the original file beofore you copy.

```
sudo cp ~/Downloads/DisplayProductID-59f1.plist /System/Library/Displays/Contents/Resources/Overrides/DisplayVendorID-1e6d/DisplayProductID-59f1
```

### 6. Restart and Verify the new screen resolution.

### 7.Enable System Integrity Protection

```
csrutil enable
```

### 8. Enjoy
