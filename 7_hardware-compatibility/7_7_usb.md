## 7.7\. USB

Device implementations SHOULD support USB peripheral mode and SHOULD support
USB host mode.

If a device implementation includes a USB port supporting peripheral mode:

*   The port MUST be connectable to a USB host that has a standard type-A or
type-C USB port.

*   The port SHOULD use micro-B, micro-AB or Type-C USB form factor. Existing
and new Android devices are **STRONGLY RECOMMENDED to meet these requirements**
so they will be able to upgrade to the future platform releases.

*   The port SHOULD either locate the port on the bottom of the device
(according to natural orientation) or enable software screen rotation for all
apps (including home screen), so that the display draws correctly when the
device is oriented with the port at bottom. Existing and new Android devices
are **STRONGLY RECOMMENDED to meet these requirements** so they will be able to
upgrade to future platform releases.

*   It MUST allow a USB host connected with the Android device to access the
contents of the shared storage volume using either USB mass storage or Media
Transfer Protocol.

*   It SHOULD implement the Android Open Accessory (AOA) API and specification
as documented in the Android SDK documentation, and if it is an Android
Handheld device it MUST implement the AOA API. Device implementations
implementing the AOA specification:

    *   MUST declare support for the hardware feature
[android.hardware.usb.accessory](http://developer.android.com/guide/topics/connectivity/usb/accessory.html).

    *   MUST support establishing an [AOA protocol based
communication](http://source.android.com/devices/accessories/aoa.html) on first
time connection with a USB host machine that acts as an accessory, without the
need for the user to change the default USB mode.

    *   MUST implement the [USB audio
class](http://developer.android.com/reference/android/hardware/usb/UsbConstants.html#USB_CLASS_AUDIO)as
documented in the Android SDK documentation.

    *   The USB mass storage class MUST include the string "android" at the end
of the interface description `iInterface` string of the USB mass storage

*   It SHOULD implement support to draw 1.5 A current during HS chirp and
traffic as specified in the [USB Battery Charging specification, revision
1.2](http://www.usb.org/developers/docs/devclass_docs/BCv1.2_070312.zip).
Existing and new Android devices are **STRONGLY RECOMMENDED to meet these
requirements** so they will be able to upgrade to the future platform releases.

*   The value of iSerialNumber in USB standard device descriptor MUST be equal
to the value of android.os.Build.SERIAL.

If a device implementation includes a USB port supporting host mode, it:

*   SHOULD use a type-C USB port, if the device implementation supports USB
3.1.

*   MAY use a non-standard port form factor, but if so MUST ship with a cable
or cables adapting the port to a standard type-A or type-C USB port.

*   MAY use a micro-AB USB port, but if so SHOULD ship with a cable or cables
adapting the port to a standard type-A or type-C USB port.

*   is **STRONGLY RECOMMENDED** to implement the [USB audio
class](http://developer.android.com/reference/android/hardware/usb/UsbConstants.html#USB_CLASS_AUDIO)
as documented in the Android SDK documentation.

*   MUST implement the Android USB host API as documented in the Android SDK,
and MUST declare support for the hardware feature
[android.hardware.usb.host](http://developer.android.com/guide/topics/connectivity/usb/host.html).

*   SHOULD support the Charging Downstream Port output current range of 1.5 A ~ 5 A as specified in the [USB Battery Charging specifications, revision 1.2](http://www.usb.org/developers/docs/devclass_docs/BCv1.2_070312.zip).
