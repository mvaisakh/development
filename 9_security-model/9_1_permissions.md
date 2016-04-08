## 9.1\. Permissions

Device implementations MUST support the [Android permissions
model](http://developer.android.com/guide/topics/security/permissions.html) as
defined in the Android developer documentation. Specifically, implementations
MUST enforce each permission defined as described in the SDK documentation; no
permissions may be omitted, altered, or ignored. Implementations MAY add
additional permissions, provided the new permission ID strings are not in the
android.\* namespace.

Permissions with a protection level of dangerous are runtime permissions.
Applications with targetSdkVersion > 22 request them at runtime. Device
implementations:

*   MUST show a dedicated interface for the user to decide whether to grant the
requested runtime permissions and also provide an interface for the user to
manage runtime permissions.
*   MUST have one and only one implementation of both user interfaces.
*   MUST NOT grant any runtime permissions to preinstalled apps unless:
    *   the user's consent can be obtained before the application uses it
    *   the runtime permissions are associated with an intent pattern for which
the preinstalled application is set as the default handler

