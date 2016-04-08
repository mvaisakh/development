## 9.9\. Full-Disk Encryption

<div class="note">

Optional for Android device implementations without a lock screen.

</div>

If the device implementation supports a secure lock screen reporting "`true`"
for [KeyguardManager.isDeviceSecure()](http://developer.android.com/reference/android/app/KeyguardManager.html#isDeviceSecure()),
and is not a device with restricted memory as reported through the
ActivityManager.isLowRamDevice() method, then the device MUST support full-disk
[encryption](http://source.android.com/devices/tech/security/encryption/index.html)
of the application private data (/data partition), as well as the application
shared storage partition (/sdcard partition) if it is a permanent,
non-removable part of the device.

For device implementations supporting full-disk encryption and with Advanced
Encryption Standard (AES) crypto performance above 50MiB/sec, the full-disk
encryption MUST be enabled by default at the time the user has completed the
out-of-box setup experience. If a device implementation is already launched on
an earlier Android version with full-disk encryption disabled by default, such
a device cannot meet the requirement through a system software update and thus
MAY be exempted.

Encryption MUST use AES with a key of 128-bits (or greater) and a mode designed
for storage (for example, AES-XTS, AES-CBC-ESSIV). The encryption key MUST NOT
be written to storage at any time without being encrypted. Other than when in
active use, the encryption key SHOULD be AES encrypted with the lockscreen
passcode stretched using a slow stretching algorithm (e.g. PBKDF2 or scrypt).
If the user has not specified a lockscreen passcode or has disabled use of the
passcode for encryption, the system SHOULD use a default passcode to wrap the
encryption key. If the device provides a hardware-backed keystore, the password
stretching algorithm MUST be cryptographically bound to that keystore. The
encryption key MUST NOT be sent off the device (even when wrapped with the user
passcode and/or hardware bound key). The upstream Android Open Source project
provides a preferred implementation of this feature based on the Linux kernel
feature dm-crypt.

