## AMCoreAudio

[![Version](http://cocoapod-badges.herokuapp.com/v/AMCoreAudio/badge.png)](http://cocoadocs.org/docsets/AMCoreAudio)
[![Platform](http://cocoapod-badges.herokuapp.com/p/AMCoreAudio/badge.png)](http://cocoadocs.org/docsets/AMCoreAudio)

`AMCoreAudio` is an Objective-C wrapper for [Apple's Core Audio](https://developer.apple.com/library/mac/documentation/musicaudio/Conceptual/CoreAudioOverview/WhatisCoreAudio/WhatisCoreAudio.html) framework focusing on:

- Simplifying audio device enumeration
- Providing accessors for the most relevant audio device properties (i.e., device name, device manufacturer, device UID, volume, mute, sample rate, clock source, etc.)
- Subscribing to system and audio device specific notifications using the delegate pattern.

`AMCoreAudio` is currently powering [AudioMate](http://audiomateapp.com) (recently open-sourced and available at https://github.com/sonicbee9/AudioMate).

### Requirements

* Mac OS X 10.7 or later
* 64-bit

### Delegates

#### AMCoreAudioHardwareDelegate

```obj-c
- (void)hardwareDeviceListChanged:(id)sender;
```
Called whenever the list of audio devices in the system changes.

**Note:** If you want to receive notifications when the list of owned audio devices on *Aggregate Devices* and *Multi-Output Devices* changes, then try using `AMCoreAudioDevice` notifications instead.

```obj-c
- (void)hardwareDefaultInputDeviceChanged:(id)sender;
```

Called whenever the system's default input device changes.

```obj-c
- (void)hardwareDefaultOutputDeviceChanged:(id)sender;
```
Called whenever the system's default output device changes.

```obj-c
- (void)hardwareDefaultSystemDeviceChanged:(id)sender;
```
Called whenever the system's default device changes.

*(This is the audio device used for alerts, sound effects, etc.)*

#### AMCoreAudioDeviceDelegate

```obj-c
- (void)audioDeviceNominalSampleRateDidChange:(id)sender;
```
Called whenever the audio device's sample rate changes.

```obj-c
- (void)audioDeviceAvailableNominalSampleRatesDidChange:(id)sender;
```
Called whenever the audio device's list of nominal sample rates changes.

**Note:** This will typically happen on *Aggregate Devices* and *Multi-Output Devices* when adding or removing other audio devices (either physical or virtual).

```obj-c
- (void)audioDeviceClockSourceDidChange:(id)sender forChannel:(UInt32)channel andDirection:(AMCoreAudioDirection)direction;
```
Called whenever the audio device's clock source changes for a given channel and direction.

```obj-c
- (void)audioDeviceNameDidChange:(id)sender;
```
Called whenever the audio device's name changes.

```obj-c
- (void)audioDeviceListDidChange:(id)sender;
```
Called whenever the list of owned audio devices on this audio device changes.

**Note:** This will typically happen on *Aggregate Devices* and *Multi-Output Devices* when adding or removing other audio devices (either physical or virtual).

```obj-c
- (void)audioDeviceVolumeDidChange:(id)sender forChannel:(UInt32)channel andDirection:(AMCoreAudioDirection)direction;
```
Called whenever the audio device's volume for a given channel and direction changes.

```obj-c
- (void)audioDeviceMuteDidChange:(id)sender forChannel:(UInt32)channel andDirection:(AMCoreAudioDirection)direction;
```
Called whenever the audio device's mute state for a given channel and direction changes.

### Further Development & Patches

Do you want to contribute to the project? Please fork, patch, and then submit a pull request!

### Sample Projects

* [AudioMate](https://github.com/sonicbee9/AudioMate) (a full-featured app recently open-sourced.)

### License

`AMCoreAudio` was written by Ruben Nine ([@sonicbee9](https://twitter.com/sonicbee9)) in 2013-2014 (open-sourced in March 2014) and is licensed under the [MIT](http://opensource.org/licenses/MIT) license. See [LICENSE.md](LICENSE.md).
