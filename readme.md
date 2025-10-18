# Dusk Downgrade: Automatic iOS 10-15 Downgrade Tool For A9 and A10 iDevices.

_By Alex Free_

Apple sunsets your iDevice? Introducing Dusk Downgrade. A completely automatic solution that tether downgrades to iOS 10-iOS 15 for A9 and A10 devices. Made possible by the work of many [others](#credits).

* There's many things you can do on iOS 10+ that perhaps you didn't think you still could, here's just a [few](#interesting-things-to-do-on-legacy-ios).

* To find out what iOS version is right for you to downgrade to, please check the [Important Info](#important-info) section.

* Please check the [FAQ](#faq) section for more information and solutions. If you have an issue, please open a [Github issue](https://github.com/alex-free/dusk-downgrade/issues/new?template=issue.md) and fill out the information.

Supported devices:

* iPhone 6S.
* iPhone 6S Plus.
* iPhone SE.
* iPhone 7.
* iPhone 7 Plus.

| [Github](https://github.com/alex-free/dusk-downgrade) | [Homepage](https://github.com/alex-free/dusk-downgrade) |

# Table Of Contents

* [Downloads](#downloads)
* [Important Info](#important-info)
* [Usage](#usage)
* [FAQ](#faq)
* [Credits](#credits)
* [License](#license)
* [Building](build.md)

## Downloads

### Version 2.0 (10/18/2025)

* [dusk-downgrade-v2.0.zip](https://github.com/alex-free/dusk-downgrade/releases/download/v2.0/dusk-downgrade-v2.0.zip) _For Mac OS and for Linux_

Dusk Downgrade is designed to work on Debian, Fedora, and Mac OS 10.12 or newer. x86_64 and ARM64 arches are supported.

Changes:

* Official A10 support! iPhone 7 and iPhone 7 Plus that is...

* Removed redundant usbmuxd resets.

* Better `$PATH` handling in boot script. Fixes for tethered restore boots.

* Cleaner interface, silenced USBMUXD on Linux.

[Previous versions](changelog.md)

## Important Info

* If you have an A10 device and restore to iOS 10, you may have baseband/cellular/activation issues. If you can activate and have baseband issues, you can of course enable airplane mode and just use WiFi. iOS 11 and up do not have any of these problems, and neither does A9 on iOS 10 or any version.

* When restoring iOS 11 or iOS 10, espically on A10, it may fail many times when booting or restoring... It really does work eventually!

## Requirements

Mac requirements:

* Mac OS 10.12 or newer.

* Either the [MacPorts](https://www.macports.org/install.php) or [Homebrew](https://brew.sh/) package manager installed.

Linux requirements:

* Fedora or Debian Linux (x86_64 or arm64).

## Usage

1) Download the latest release and extract it.

2) Execute it in Terminal (this is a command line program). Drag the `dusk` command into your Terminal window and press enter. Or if you want, cd into the extracted release and:

`./dusk <drag your ipsw file here>`

Note that on Linux you must run `dusk` with root privilages, i.e. `sudo ./dusk <drag your ipsw file here>`. On Mac you do not need to do this.

3) Follow the prompts.

## Interesting Things To Do On Legacy iOS

* Instagram still works from the AppStore.

* YouTube in Safari works. When you get an AD, refresh and it goes away!

* You can send/recieve FaceTime calls and iMessages to your main iPhone.

* You can use it as your main iPhone (I did for a few weeks on a 6S Plus). T-Mobile/Mint Mobile in the USA are confirmed working carriers for even the lowest iOS this supports.

## FAQ

### My iPhone Won't Detect On Fedora Linux

This may happen the first time you ever use Dusk Downgrade on Fedora Linux. Reboot your computer, and try Dusk Downgrade again. 

### Stuck on Checkmate?

Disconnect and reconnect the lightning cable to get past it.

### Error Failed To Open Handle (No Device) After Checkmate?

It appears on Linux for A10 this can appear and "fix itself". For A9 not so much.... Disconnect and reconnect the lightning cable to get past it if A9. The error will appear again but be non-fatal and work.

### Unable To Successfully Restore Device

Wait until your prompted to enter DFU Mode again, and before you do disconnect and reconnect the lightning cable. The next restore should work.

### How Do I Boot My Downgraded iPhone If The Battery Dies Or I Turn It Off?

In the same folder that the `dusk` command is in, there will be a new command starting with `boot` which is generated after a successful downgrade automatically. All you have to do is execute that command starting with `boot` while your iPhone is in Recovery Mode and connected to your computer.

### Why Is My iPhone Not Detected?

Make sure your using a USB-A to lightning cable. If you have to, you can also use a USB-C to USB-A adapter with the USB-A lightning cable plugged into it. If you are using a USBA-A lightning cable correctly, try unplugging the cable and then plugging it back in. Then execute `dusk` again.

### Why Does It Take So Long? You Say It's Much Faster The Next Time You Run It?

On the first run of Dusk Downgrade, there are many additional steps in the proccess that will trigger automatically for you. **Subsequent runs will be signifigantly shorter and take fewer steps as it caches needed data from the first run locally in the `data` folder.** That `data` folder is very important and personalized to your iPhone. You should back it up because you can put it back in any future dusk downgrade release and it will use that data when it detects your iPhone!

Similar to the data folder are the `boot*` scripts. These get generated once your iPhone downgrades successfully automatically, and are also personalized to your iPhone and should be backed up so you can reboot the iPhone from Recovery Mode if it dies or your turn it off.

You can also use the `dusk` command to transfer your `data` and `boot*` files from a previous release of Dusk Downgrade:

`./dusk -u <path to new update of Dusk Downgrade>`

### How Are Errors Handled?

Certian aspects of Turdus_ra1n (exploiting SEP, booting exploited iOS) can fail the first time. This is why Dusk Downgrade has very extensive if-fail-then-retry logic. It will eventually work, and it won't continue the proccess until it does. So don't be discouraged when it says `Something went wrong, lets try that again` because it's really just working as intended and trying again (sometimes many times to get that PTEBlock) does eventually work out. One exception to this is if turdusra1n/turdus_merula crashes at `- <Log> checkm8 setup stage`. If your stuck here for a long time (more then 30 seconds) I would `ctrl+c` to exit dusk downgrade, unpulg the USB-A to Lightning cable from the USB port on the Mac, then plug it back in before running the `dusk` command again. Unfortunately I don't have a better solution for this yet as it is a turdus merula problem. In a similar vein to above, if you fail to enter DFU mode when prompted or the custom ramdisk fails to boot dusk downgrade notices this and goes back to correct it.

### What Has Dusk Downgrade Been Tested On?

I have extensively tested Dusk Downgrade with 2 different iPhone 6S Pluses with MacBook Airs on Mac OS 12 as well as a Mac mini on Mac OS 10.12. It is reported to work on even the latest Mac OS. Linux support was developed on Fedora Linux.

## Credits

* [Sep.lol team](https://sep.lol/) for turdus merula.

* [LukeZGD](https://github.com/LukeZGD) for [Legacy-iOS-Kit](https://github.com/LukeZGD/Legacy-iOS-Kit).

## License

Dusk Downgrade itself is released under the 3-BSD license, see [license.md](license.md). Dusk Downgrade uses many other dependency programs which are not under that license, such as:

* Turdus Merula (closed source, open source is planned).

* Legacy-iOS-Kit (GNU GPL v3.0). This uses my [forked version](https://github.com/alex-free/Legacy-iOS-Kit) by the way.