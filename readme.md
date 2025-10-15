# Dusk Downgrade: Automatic iOS 10-15 Downgrade Tool For A9 and A10 iDevices.

_By Alex Free_

What happens after Apple sunsets your iDevice? Introducing Dusk Downgrade. A completely automatic solution that tether downgrades to iOS 10-iOS 15 for A9 and A10 devices. Made possible by the work of many [others](#credits). For iOS 9, check out my [github](https://github.com/alex-free) as I have a very similar tool dedicated for iOS 9 A9.

* There's many things you can do on iOS 10+ that perhaps you didn't think you still could, here's just a [few](#interesting-things-to-do-on-legacy-ios).

* To find out what iOS version is right for you to downgrade to, please check the [Important Info](#important-info) section.

* Please check the [FAQ](#faq) section for more information and solutions. If you have an issue, please open a [Github issue](https://github.com/alex-free/dusk-downgrade/issues/new?template=issue.md) and fill out the information.

Officially supported devices:

* iPhone 6S.
* iPhone 6S Plus.
* iPhone SE.

The following devices should work in theory. I have wrote special support functions for them, but can not test until I actually get them in a few days. Please respond to me on reddit or in a [Github issue](https://github.com/alex-free/dusk-downgrade/issues/new?template=issue.md) if you have such a device. Sorry I am impulsive, everything is done I'm just waiting on the A10 hardware to verify it works as it should. I'm sure we can debug any issues if they occur.

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

### Version 1.0 (10/14/2025)

* [dusk-downgrade-v1.0.zip](https://github.com/alex-free/dusk-downgrade/releases/download/v1.0/dusk-downgrade-v1.0.zip) _For Mac OS and for Linux_

Dusk Downgrade is designed to work on Debian, Fedora, and Mac OS 10.12 or newer. x86_64 and ARM64 arches are supported.

Changes:

* Initial release.

## Important Info

If you have an A10 device and restore to iOS 10, you may have baseband/cellular/activation issues. If you can activate and have baseband issues, you can of course enable airplane mode and just use WiFi. iOS 11 and up do not have any of these problems, and neither does A9 on iOS 10 or any version.

## Requirements

Mac requirements:

* Mac OS 10.12 or newer.

* Either the [MacPorts](https://www.macports.org/install.php) or [Homebrew](https://brew.sh/) package manager installed.

Linux requirements:

* Fedora or Debian Linux (x86_64 or arm64).

## Usage

1) Download the latest release and extract it.

2) Execute it in Terminal (this is a command line program). Drag the `dusk` command into your Terminal window and press enter. Or if you want, cd into the extracted release and:

`./dusk`

Note that on Linux you must run `a999` with root privilages, i.e. `sudo ./dusk`. On Mac you do not need to do this.

3) Follow the prompts.

## Interesting Things To Do On Legacy iOS

* Instagram still works from the AppStore.

* YouTube in Safari works.

* You can send/recieve FaceTime calls and iMessages to your main iPhone.

* You can use it as your main iPhone (I did for a few weeks). T-Mobile/Mint Mobile in the USA are confirmed working carriers for even the lowest iOS this supports.

## FAQ

### My iPhone Won't Detect On Fedora Linux

This may happen the first time you ever use Dusk Downgrade on Fedora Linux. Reboot your computer, and try Dusk Downgrade again. 

### Stuck on Checkmate?

Disconnect and reconnect the lightning cable to get past it.

### Error Failed To Open Handle (No Device) After Checkmate?

This error occurs on Linux when booting iOS 9. Disconnect and reconnect the lightning cable to get past it. The error will appear again but be non-fatal and work.

### Unable To Successfully Restore Device

Wait until your prompted to enter DFU Mode again, and before you do disconnect and reconnect the lightning cable. The next restore should work.

### How Do I Boot My Downgraded iPhone If The Battery Dies Or I Turn It Off?

In the same folder that the `dusk` command is in, there will be a new command starting with `boot` which is generated after a successful downgrade automatically. All you have to do is execute that command starting with `boot` while your iPhone is in Recovery Mode and connected to your computer.

### Why Is My iPhone Not Detected?

Make sure your using a USB-A to lightning cable. If you have to, you can also use a USB-C to USB-A adapter with the USB-A lightning cable plugged into it. If you are using a USBA-A lightning cable correctly, try unplugging the cable and then plugging it back in. Then execute `a999` again.

### Why Does It Take So Long? You Say It's Much Faster The Next Time You Run It?

On the first run of Dusk Downgrade, there are many additional steps in the proccess that will trigger automatically for you. **Subsequent runs will be signifigantly shorter and take fewer steps as it caches needed data from the first run locally in the `data` folder.** That `data` folder is very important and personalized to your iPhone. You should back it up because you can put it back in any future a999activator release and it will use that data when it detects your iPhone!

Similar to the data folder are the `boot*` scripts. These get generated once your iPhone downgrades successfully automatically, and are also personalized to your iPhone and should be backed up so you can reboot the iPhone from Recovery Mode if it dies or your turn it off.

You can also use the `dusk` command to transfer your `data` and `boot*` files from a previous release of Dusk Downgrade:

`./dusk -u <path to new update of Dusk Downgrade>`

### How Are Errors Handled?

Certian aspects of Turdus_ra1n (exploiting SEP, booting exploited iOS) can fail the first time. This is why A999activator has very extensive if-fail-then-retry logic. It will eventually work, and it won't continue the proccess until it does. So don't be discouraged when it says `Something went wrong, lets try that again` because it's really just working as intended and trying again (sometimes many times to get that PTEBlock) does eventually work out. One exception to this is if turdusra1n/turdus_merula crashes at `- <Log> checkm8 setup stage`. If your stuck here for a long time (more then 30 seconds) I would `ctrl+c` to exit a999activator, unpulg the USB-A to Lightning cable from the USB port on the Mac, then plug it back in before running the `dusk` command again. Unfortunately I don't have a better solution for this yet as it is a turdus merula problem. In a similar vein to above, if you fail to enter DFU mode when prompted or the custom ramdisk fails to boot a999activator notices this and goes back to correct it.

### What Has Dusk Downgrade Been Tested On?

I have extensively tested Dusk Downgrade with 2 different iPhone 6S Pluses with MacBook Airs on Mac OS 12 as well as a Mac mini on Mac OS 10.12. It is reported to work on even the latest Mac OS. Linux support was developed on Fedora Linux.

### What About iPads with A9(X)?

iPads in theory can work too in a future update, as well as any other A9 device not currently supported.

## Credits

* [Sep.lol team](https://sep.lol/) for turdus merula.

* [LukeZGD](https://github.com/LukeZGD) for [Legacy-iOS-Kit](https://github.com/LukeZGD/Legacy-iOS-Kit).

## License

Dusk Downgrade itself is released under the 3-BSD license, see [license.md](license.md). Dusk Downgrade uses many other dependency programs which are not under that license, such as:

* Turdus Merula (closed source, open source is planned).

* Legacy-iOS-Kit (GNU GPL v3.0). This uses my [forked version](https://github.com/alex-free/Legacy-iOS-Kit) by the way.