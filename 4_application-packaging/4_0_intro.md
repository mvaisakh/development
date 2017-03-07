# 4\. Application Packaging Compatibility

Device implementations MUST install and run Android “.apk” files as generated
by the “aapt” tool included in the [official Android SDK](http://developer.android.com/tools/help/index.html).
For this reason device implementations SHOULD use the reference implementation’s
package management system.

The package manager MUST support verifying “.apk” files using the
[APK Signature Scheme v2](https://source.android.com/security/apksigning/v2.html)
and [JAR signing](https://source.android.com/security/apksigning/v2.html#v1-verification).

Devices implementations MUST NOT extend either the
[.apk](http://developer.android.com/guide/components/fundamentals.html),
[Android Manifest](http://developer.android.com/guide/topics/manifest/manifest-intro.html),
[Dalvik bytecode](https://android.googlesource.com/platform/dalvik/), or
RenderScript bytecode formats in such a way that would prevent those files from
installing and running correctly on other compatible devices.
