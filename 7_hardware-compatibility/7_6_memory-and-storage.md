## 7.6\. Memory and Storage

### 7.6.1\. Minimum Memory and Storage

<div class="note">

Android Television devices MUST have at least 5GB of non-volatile storage
available for application private data.

</div>

The memory available to the kernel and userspace on device implementations MUST
be at least equal or larger than the minimum values specified by the following
table. (See [section 7.1.1](#7_1_1_screen_configuration) for screen size and
density definitions.)

<table>
 <tr>
    <th>Density and screen size</th>
    <th>32-bit device</th>
    <th>64-bit device</th>
 </tr>
 <tr>
    <td>Android Watch devices (due to smaller screens)</td>
    <td>416MB</td>
    <td>Not applicable</td>
 </tr>
 <tr>
    <td><ul>
    <li class="table_list">280dpi or lower on small/normal screens</li>
    <li class="table_list">mdpi or lower on large screens</li>
    <li class="table_list">ldpi or lower on extra large screens</li>
    </ul></td>
    <td>424MB</td>
    <td>704MB</td>
 </tr>
 <tr>
    <td><ul>
    <li class="table_list">xhdpi or higher on small/normal screens</li>
    <li class="table_list">hdpi or higher on large screens</li>
    <li class="table_list">mdpi or higher on extra large screens</li></ul></td>
    <td>512MB</td>
    <td>832MB</td>
 </tr>
 <tr>
    <td><ul>
    <li class="table_list">400dpi or higher on small/normal screens</li>
    <li class="table_list">xhdpi or higher on large screens</li>
     <li class="table_list">tvdpi or higher on extra large screens</li></ul></td>
    <td>896MB</td>
    <td>1280MB</td>
 </tr>
 <tr>
    <td><ul>
    <li class="table_list">560dpi or higher on small/normal screens</li>
    <li class="table_list">400dpi or higher on large screens</li>
    <li class="table_list">xhdpi or higher on extra large screens</li></ul></td>
    <td>1344MB</td>
    <td>1824MB</td>
 </tr>
</table>

The minimum memory values MUST be in addition to any memory space already
dedicated to hardware components such as radio, video, and so on that is not
under the kernel’s control.

Device implementations with less than 512MB of memory available to the kernel
and userspace, unless an Android Watch, MUST return the value "true" for
ActivityManager.isLowRamDevice().

Android Television devices MUST have at least 5GB and other device
implementations MUST have at least 1.5GB of non-volatile storage available for
application private data. That is, the /data partition MUST be at least 5GB for
Android Television devices and at least 1.5GB for other device implementations.
Device implementations that run Android are **STRONGLY RECOMMENDED** to have at
least 3GB of non-volatile storage for application private data so they will be
able to upgrade to the future platform releases.

The Android APIs include a [Download
Manager](http://developer.android.com/reference/android/app/DownloadManager.html)
that applications MAY use to download data files. The device implementation of
the Download Manager MUST be capable of downloading individual files of at
least 100MB in size to the default “cache” location.

### 7.6.2\. Application Shared Storage

Device implementations MUST offer shared storage for applications also often
referred as “shared external storage”.

Device implementations MUST be configured with shared storage mounted by
default, “out of the box”. If the shared storage is not mounted on the
Linuxpath /sdcard, then the device MUST include a Linux symbolic link from
/sdcard to the actual mount point.

Device implementations MAY have hardware for user-accessible removable storage,
such as a Secure Digital (SD) card slot. If this slot is used to satisfy the
shared storage requirement, the device implementation:

*   MUST implement a toast or pop-up user interface warning the user when there
is no SD card.
*   MUST include a FAT-formatted SD card 1GB in size or larger OR show on the
box and other material available at time of purchase that the SD card has to be
separately purchased.
*   MUST mount the SD card by default.

Alternatively, device implementations MAY allocate internal (non-removable)
storage as shared storage for apps as included in the upstream Android Open
Source Project; device implementations SHOULD use this configuration and
software implementation. If a device implementation uses internal
(non-removable) storage to satisfy the shared storage requirement, while that
storage MAY share space with the application private data, it MUST be at least
1GB in size and mounted on /sdcard (or /sdcard MUST be a symbolic link to the
physical location if it is mounted elsewhere).

Device implementations MUST enforce as documented the
android.permission.WRITE_EXTERNAL_STORAGE permission on this shared storage.
Shared storage MUST otherwise be writable by any application that obtains that
permission.

Device implementations that include multiple shared storage paths (such as both
an SD card slot and shared internal storage) MUST allow only pre-installed &amp;
privileged Android applications with the WRITE_EXTERNAL_STORAGE permission to
write to the secondary external storage, except when writing to their
package-specific directories or within the `URI` returned by firing the
`ACTION_OPEN_DOCUMENT_TREE` intent.

However, device implementations SHOULD expose content from both storage paths
transparently through Android’s media scanner service and
android.provider.MediaStore.

Regardless of the form of shared storage used, if the device implementation has
a USB port with USB peripheral mode support, it MUST provide some mechanism to
access the contents of shared storage from a host computer. Device
implementations MAY use USB mass storage, but SHOULD use Media Transfer
Protocol to satisfy this requirement. If the device implementation supports
Media Transfer Protocol, it:

*   SHOULD be compatible with the reference Android MTP host, [Android File
Transfer](http://www.android.com/filetransfer).
*   SHOULD report a USB device class of 0x00.
*   SHOULD report a USB interface name of 'MTP'.

### 7.6.3\. Adoptable Storage

Device implementations are STRONGLY RECOMMENDED to implement [adoptable
storage](http://source.android.com/devices/storage/adoptable.html) if the
removable storage device port is in a long-term stable location, such as within
the battery compartment or other protective cover.

Device implementations such as a television, MAY enable adoption through USB
ports as the device is expected to be static and not mobile. But for other
device implementations that are mobile in nature, it is STRONGLY RECOMMENDED to
implement the adoptable storage in a long-term stable location, since
accidentally disconnecting them can cause data loss/corruption.

## 7.7\. USB

Device implementations SHOULD support USB peripheral mode and SHOULD support
USB host mode.

If a device implementation includes a USB port supporting peripheral mode:

*   The port MUST be connectable to a USB host that has a standard type-A or type-C USB port.
*   The port SHOULD use micro-B, micro-AB or Type-C USB form factor. Existing and new Android devices are **STRONGLY RECOMMENDED to meet these requirements** so they will be able to upgrade to the future platform releases.
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

*   SHOULD use a type-C USB port, if the device implementation supports USB 3.1.
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
*   SHOULD support the Charging Downstream Port output current range of 1.5 A ~
5 A as specified in the [USB Battery Charging specifications, revision
1.2](http://www.usb.org/developers/docs/devclass_docs/BCv1.2_070312.zip).
