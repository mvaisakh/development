## 9.11\. Keys and Credentials

The [Android Keystore
System](https://developer.android.com/training/articles/keystore.html) allows
app developers to store cryptographic keys in a container and use them in
cryptographic operations through the [KeyChain
API](https://developer.android.com/reference/android/security/KeyChain.html) or
the [Keystore API](https://developer.android.com/reference/java/security/KeyStore.html).

All Android device implementations MUST meet the following requirements:

*   SHOULD not limit the number of keys that can be generated, and MUST at
least allow more than 8,192 keys to be imported. 
*   The lock screen authentication MUST rate limit attempts and SHOULD have an
    exponential backoff algorithm as implemented in the Android Open Source
    Project.
*   When the device implementation supports a secure lock screen and has a
secure hardware such as a Secure Element (SE) where a Trusted Execution
Environment (TEE) can be implemented, then it:
    *   Is STRONGLY RECOMMENDED to back up the keystore implementation with the
secure hardware. The upstream Android Open Source Project provides the
Keymaster Hardware Abstraction Layer (HAL) implementation that can be used to
satisfy this requirement.
    *   MUST perform the lock screen authentication in the secure hardware if
the device has a hardware-backed keystore implementation and only when
successful allow the authentication-bound keys to be used. The upstream Android
Open Source Project provides the [Gatekeeper Hardware Abstraction Layer
(HAL)](http://source.android.com/devices/tech/security/authentication/gatekeeper.html)
that can be used to satisfy this requirement.

Note that while the above TEE-related requirements are stated as STRONGLY
RECOMMENDED, the Compatibility Definition for the next API version is planned
to changed these to REQIUIRED. If a device implementation is already launched
on an earlier Android version and has not implemented a trusted operating
system on the secure hardware, such a device might not be able to meet the
requirements through a system software update and thus is STRONGLY RECOMMENDED
to implement a TEE.

