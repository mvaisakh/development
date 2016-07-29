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
*   The lock screen authentication MUST rate limit attempts and MUST have an
    exponential backoff algorithm. Beyond 150 failed attempts, the delay MUST be
    at least 24 hours per attempt.
*   When the device implementation supports a secure lock screen it MUST back up the
    keystore implementation with secure hardware and meet following requirements:
    *   MUST have hardware backed implementations of RSA, AES, ECDSA and HMAC cryptographic
    algorithms and MD5, SHA1, SHA-2 Family hash functions to properly support the
    [Android Keystore system's supported algorithms]
    (https://developer.android.com/training/articles/keystore.html#SupportedAlgorithms).
    *   MUST perform the lock screen authentication in the secure hardware and only when
    successful allow the authentication-bound keys to be used. The upstream Android
    Open Source Project provides the [Gatekeeper Hardware Abstraction Layer
    (HAL)](http://source.android.com/devices/tech/security/authentication/gatekeeper.html)
    that can be used to satisfy this requirement.

Note that if a device implementation is already launched on an earlier Android version, and does
not have a fingerprint scanner, such a device is exempted from the requirement to have a
hardware-backed keystore.