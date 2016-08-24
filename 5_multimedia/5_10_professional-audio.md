## 5.10\. Professional Audio

If a device implementation meets _all_ of the following requirements, it is
STRONGLY RECOMMENDED to report support for feature android.hardware.audio.pro
via the
[android.content.pm.PackageManager](http://developer.android.com/reference/android/content/pm/PackageManager.html)
class.

*   The device implementation MUST report support for feature
android.hardware.audio.low_latency.
*   The continuous round-trip audio latency, as defined in section 5.6 Audio
Latency, MUST be 20 milliseconds or less and SHOULD be 10 milliseconds or less
over at least one supported path.
*   If the device includes a 4 conductor 3.5mm audio jack, the continuous
round-trip audio latency MUST be 20 milliseconds or less over the audio jack
path, and SHOULD be 10 milliseconds or less over at the audio jack path.
*   The device implementation MUST include a USB port(s) supporting USB host
mode and USB peripheral mode.
*   The USB host mode MUST implement the USB audio class.
*   If the device includes an HDMI port, the device implementation MUST support
output in stereo and eight channels at 20-bit or 24-bit depth and 192 kHz
without bit-depth loss or resampling.
*   The device implementation MUST report support for feature
android.software.midi.
*   If the device includes a 4 conductor 3.5mm audio jack, the device
implementation is STRONGLY RECOMMENDED to comply with section [Mobile device
(jack) specifications](https://source.android.com/accessories/headset/specification.html#mobile_device_jack_specifications)
of the [Wired Audio Headset Specification (v1.1)](https://source.android.com/accessories/headset/specification.html).

Latencies and USB audio requirements MUST be met using the
[OpenSL ES](https://developer.android.com/ndk/guides/audio/opensl-for-android.html)
PCM buffer queue API.
