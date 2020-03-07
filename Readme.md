# MacOS Catalina 
##              Ultrawide monitor 2560 x 1080 setup (LG U29UM59)

Do with your own risk , not responsible for any damage to your device.

## Reference:

https://www.tonymacx86.com/threads/lg-ultrawide-29um57-p.179861/#post-1373704
https://www.tonymacx86.com/threads/adding-using-hidpi-custom-resolutions.133254/page-57
https://comsysto.github.io/Display-Override-PropertyList-File-Parser-and-Generator-with-HiDPI-Support-For-Scaled-Resolutions/


## Step:


### 1.

#### 1. Reboot the Mac and hold down Command + R keys simultaneously after you hear the startup chime, this will boot Mac OS X into Recovery Mode
#### 2. When the “MacOS Utilities” / “OS X Utilities” screen appears, pull down the ‘Utilities’ menu at the top of the screen instead, and choose “Terminal”

#### 3.Type the following command into the terminal then hit return:

```
csrutil disable; reboot
```

```
csrutil status

```

### 2.
```
sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true
```

### 3.
```
ioreg -lw0 | grep IODisplayPrefsKey
```

Output:
```
"IODisplayPrefsKey" = "IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/IGPU@2/AppleIntelFramebuffer@0/display0/AppleBacklightDisplay-610-a019"
"IODisplayPrefsKey" = "IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/IGPU@2/AppleIntelFramebuffer@2/display0/AppleDisplay-10ac-d06e"
```


### 4.

Download DisplayProductID-59f1.plist.



### 5.
```
sudo mount -uw /
```
```
sudo cp ~/Downloads/DisplayProductID-d06e.plist /System/Library/Displays/Contents/Resources/Overrides/DisplayVendorID-10ac/DisplayProductID-d06e
```

### 6.



```
csrutil enable

```
