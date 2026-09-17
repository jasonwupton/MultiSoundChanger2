<p align="center">
  <img width="350" height="276" src="https://user-images.githubusercontent.com/8312717/115996670-e6511000-a5e8-11eb-8c46-869378d4df2a.png">
</p>

## About this fork: MultiSoundChanger2

Heads up.  This is a personal rebuild of [rlxone/MultiSoundChanger](https://github.com/rlxone/MultiSoundChanger) so it runs natively on Apple Silicon.  I made it for myself and I'm sharing it as-is.  I'm not supporting it, and issues or pull requests may not get a response.

All credit for the app goes to the original author, rlxone (Dmitry Medyuho).  It's released under the same Apache 2.0 licence.

What changed from the original:

* Universal build (Apple Silicon and Intel), macOS 15 or later
* The volume popup loads Apple's system OSD framework at runtime instead of linking a bundled Intel-only copy
* Renamed to MultiSoundChanger2 with its own bundle ID (`com.jasonupton.multisoundchanger2`), so it doesn't collide with the original app's privacy settings
* Build fixes for current Xcode (deployment target and CocoaPods settings)

The Intel half builds but I haven't tested it.

### Install

1. Download `MultiSoundChanger2.zip` from this repo's Releases, unzip it, and move the app to Applications.
2. The app isn't notarized, so macOS blocks it the first time.  Open System Settings > Privacy & Security and click "Open Anyway."
3. Grant Accessibility when asked (System Settings > Privacy & Security > Accessibility).  The volume keys won't work without it.
4. Quit and reopen the app after granting.

### Troubleshooting: volume keys show a "not allowed" symbol

macOS is still holding an old permission record.  To clear it:

1. Quit MultiSoundChanger2.
2. In Terminal, run:
   `tccutil reset Accessibility com.jasonupton.multisoundchanger2`
3. Open System Settings > Privacy & Security > Accessibility, click +, add `/Applications/MultiSoundChanger2.app`, and turn it on.
4. Open MultiSoundChanger2 again.

Repeat these steps after installing a new version.

### Building from source

Needs Xcode 26 and CocoaPods.

1. `pod install`
2. Open `MultiSoundChanger.xcworkspace` and build the `MultiSoundChanger` scheme.

---

## Original README


## MultiSound Changer for MacOS
Latest release https://github.com/rlxone/MultiSoundChanger/releases

A small tool for changing sound volume **even for aggregate devices** cause native sound volume controller can't change volume of aggregate devices (it was always pain in the ass with my laptop).
 


Features:
* **Changing sound volume of every device** (even virtual aggregate device volume by changing volume of every device in aggregate device)
* Changing default output device
* Native appearance (looks like native volume controller)
* Media keys support

I think it can be very useful if you're using VoodooHDA with 4.0+ sound on the board (my use case), but you can find another use cases.

## Usage

For example if you want to play 2 or more output devices at the same time you should:
* Create aggregate device in Audio MIDI Setup
* Add all output devices you want to this new aggregate device
* Hide default sound controller icon if enabled (by dragging away or in audio preferences)
* Use our app to control sound volume
* Add our app to startup (if you need)


## Inspiration
* [retrography/audioswitch](https://github.com/retrography/audioswitch)

## Licence
* This project is released under the Apache 2.0 licence. See LICENCE
