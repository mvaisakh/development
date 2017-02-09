
## 3.2\. Soft API Compatibility

In addition to the managed APIs from [section 3.1](#3_1_managed_api_compatibility),
Android also includes a significant runtime-only “soft” API, in the form of such
things as intents, permissions, and similar aspects of Android applications that
cannot be enforced at application compile time.

### 3.2.1\. Permissions

Device implementers MUST support and enforce all permission constants as
documented by the [Permission reference page](http://developer.android.com/reference/android/Manifest.permission.html).
Note that [section 9](#9_security_model_compatibility) lists additional
requirements related to the Android security model.

### 3.2.2\. Build Parameters

The Android APIs include a number of constants on the
[android.os.Build class](http://developer.android.com/reference/android/os/Build.html)
that are intended to describe the current device. To provide consistent,
meaningful values across device implementations, the table below includes
additional restrictions on the formats of these values to which device
implementations MUST conform.

<table>
 <tr>
    <th>Parameter</th>
    <th>Details</th>
 </tr>
 <tr>
    <td>VERSION.RELEASE</td>
    <td>The version of the currently-executing Android system, in human-readable
    format. This field MUST have one of the string values defined in
    <a href="http://source.android.com/compatibility/ANDROID_VERSION/versions.html">ANDROID_VERSION</a>.</td>
 </tr>
 <tr>
    <td>VERSION.SDK</td>
    <td>The version of the currently-executing Android system, in a format
    accessible to third-party application code. For Android ANDROID_VERSION,
    this field MUST have the integer value ANDROID_VERSION_INT.</td>
 </tr>
 <tr>
    <td>VERSION.SDK_INT</td>
    <td>The version of the currently-executing Android system, in a format
    accessible to third-party application code. For Android ANDROID_VERSION,
    this field MUST have the integer value ANDROID_VERSION_INT.</td>
 </tr>
 <tr>
    <td>VERSION.INCREMENTAL</td>
    <td>A value chosen by the device implementer designating the specific build
    of the currently-executing Android system, in human-readable format. This
    value MUST NOT be reused for different builds made available to end users. A
    typical use of this field is to indicate which build number or
    source-control change identifier was used to generate the build. There are
    no requirements on the specific format of this field, except that it MUST
    NOT be null or the empty string ("").</td>
 </tr>
 <tr>
    <td>BOARD</td>
    <td>A value chosen by the device implementer identifying the specific
    internal hardware used by the device, in human-readable format. A possible
    use of this field is to indicate the specific revision of the board powering
    the device. The value of this field MUST be encodable as 7-bit ASCII and
    match the regular expression &ldquo;^[a-zA-Z0-9_-]+$&rdquo;.</td>
 </tr>
 <tr>
    <td>BRAND</td>
    <td>A value reflecting the brand name associated with the device as known to
    the end users. MUST be in human-readable format and SHOULD represent the
    manufacturer of the device or the company brand under which the device is
    marketed. The value of this field MUST be encodable as 7-bit ASCII and match
    the regular expression &ldquo;^[a-zA-Z0-9_-]+$&rdquo;.</td>
 </tr>
 <tr>
    <td>SUPPORTED_ABIS</td>
    <td>The name of the instruction set (CPU type + ABI convention) of native
    code. See <a href="#3_3_native_api_compatibility">section 3.3. Native API
    Compatibility</a>.</td>
 </tr>
 <tr>
    <td>SUPPORTED_32_BIT_ABIS</td>
    <td>The name of the instruction set (CPU type + ABI convention) of native
    code. See <a href="#3_3_native_api_compatibility">section 3.3. Native API
    Compatibility</a>.</td>
 </tr>
 <tr>
    <td>SUPPORTED_64_BIT_ABIS</td>
    <td>The name of the second instruction set (CPU type + ABI convention) of
    native code. See <a href="#3_3_native_api_compatibility">section 3.3. Native
    API Compatibility</a>.</td>
 </tr>
 <tr>
    <td>CPU_ABI</td>
    <td>The name of the instruction set (CPU type + ABI convention) of native
    code. See <a href="#3_3_native_api_compatibility">section 3.3. Native API
    Compatibility</a>.</td>
 </tr>
 <tr>
    <td>CPU_ABI2</td>
    <td>The name of the second instruction set (CPU type + ABI convention) of
    native code. See <a href="#3_3_native_api_compatibility">section 3.3. Native
    API Compatibility</a>.</td>
 </tr>
 <tr>
    <td>DEVICE</td>
    <td>A value chosen by the device implementer containing the development name
    or code name identifying the configuration of the hardware features and
    industrial design of the device. The value of this field MUST be encodable
    as 7-bit ASCII and match the regular expression
    &ldquo;^[a-zA-Z0-9_-]+$&rdquo;. This device name MUST NOT change during the
    lifetime of the product.</td>
 </tr>
 <tr>
    <td>FINGERPRINT</td>
    <td>A string that uniquely identifies this build. It SHOULD be reasonably
    human-readable. It MUST follow this template:
    <p class="small">$(BRAND)/$(PRODUCT)/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;$(DEVICE):$(VERSION.RELEASE)/$(ID)/$(VERSION.INCREMENTAL):$(TYPE)/$(TAGS)</p>
    <p>For example:</p>
<p class="small">acme/myproduct/<br>
      &nbsp;&nbsp;&nbsp;&nbsp;mydevice:ANDROID_VERSION/LMYXX/3359:userdebug/test-keys</p>
      <p>The fingerprint MUST NOT include whitespace characters. If other fields
      included in the template above have whitespace characters, they MUST be
      replaced in the build fingerprint with another character, such as the
      underscore ("_") character. The value of this field MUST be encodable as
      7-bit ASCII.</p></td>
 </tr>
 <tr>
    <td>HARDWARE</td>
    <td>The name of the hardware (from the kernel command line or /proc). It
    SHOULD be reasonably human-readable. The value of this field MUST be
    encodable as 7-bit ASCII and match the regular expression
    &ldquo;^[a-zA-Z0-9_-]+$&rdquo;.</td>
 </tr>
 <tr>
    <td>HOST</td>
    <td>A string that uniquely identifies the host the build was built on, in
    human-readable format. There are no requirements on the specific format of
    this field, except that it MUST NOT be null or the empty string ("").</td>
 </tr>
 <tr>
    <td>ID</td>
    <td>An identifier chosen by the device implementer to refer to a specific
    release, in human-readable format. This field can be the same as
    android.os.Build.VERSION.INCREMENTAL, but SHOULD be a value sufficiently
    meaningful for end users to distinguish between software builds. The value
    of this field MUST be encodable as 7-bit ASCII and match the regular
    expression &ldquo;^[a-zA-Z0-9._-]+$&rdquo;.</td>
 </tr>
 <tr>
    <td>MANUFACTURER</td>
    <td>The trade name of the Original Equipment Manufacturer (OEM) of the
    product. There are no requirements on the specific format of this field,
    except that it MUST NOT be null or the empty string ("").</td>
 </tr>
 <tr>
    <td>MODEL</td>
    <td>A value chosen by the device implementer containing the name of the
    device as known to the end user. This SHOULD be the same name under which
    the device is marketed and sold to end users. There are no requirements on
    the specific format of this field, except that it MUST NOT be null or the
    empty string ("").</td>
 </tr>
 <tr>
    <td>PRODUCT</td>
    <td>A value chosen by the device implementer containing the development name
    or code name of the specific product (SKU) that MUST be unique within the
    same brand. MUST be human-readable, but is not necessarily intended for view
    by end users. The value of this field MUST be encodable as 7-bit ASCII and
    match the regular expression &ldquo;^[a-zA-Z0-9_-]+$&rdquo;. This product
    name MUST NOT change during the lifetime of the product.</td>
 </tr>
 <tr>
    <td>SERIAL</td>
    <td>A hardware serial number, which MUST be available and unique across
    devices with the same MODEL and MANUFACTURER. The value of this field MUST
    be encodable as 7-bit ASCII and match the regular expression
    &ldquo;^([a-zA-Z0-9]{6,20})$&rdquo;.</td>
 </tr>
 <tr>
    <td>TAGS</td>
    <td>A comma-separated list of tags chosen by the device implementer that
    further distinguishes the build. This field MUST have one of the values
    corresponding to the three typical Android platform signing configurations:
    release-keys, dev-keys, test-keys.</td>
 </tr>
 <tr>
    <td>TIME</td>
    <td>A value representing the timestamp of when the build occurred.</td>
 </tr>
 <tr>
    <td>TYPE</td>
    <td>A value chosen by the device implementer specifying the runtime
    configuration of the build. This field MUST have one of the values
    corresponding to the three typical Android runtime configurations: user,
    userdebug, or eng.</td>
 </tr>
 <tr>
    <td>USER</td>
    <td>A name or user ID of the user (or automated user) that generated the
    build. There are no requirements on the specific format of this field,
    except that it MUST NOT be null or the empty string ("").</td>
 </tr>
 <tr>
    <td>SECURITY_PATCH</td>
    <td>A value indicating the security patch level of a build. It MUST signify
    that the build includes all security patches issued up through the
    designated Android Public Security Bulletin. It MUST be in the format
    [YYYY-MM-DD], matching one of the Android Security Patch Level strings of
    the <a href="source.android.com/security/bulletin"> Public Security
    Bulletins</a>, for example "2015-11-01".</td>
 </tr>
 <tr>
    <td>BASE_OS</td>
    <td>A value representing the FINGERPRINT parameter of the build that is
    otherwise identical to this build except for the patches provided in the
    Android Public Security Bulletin. It MUST report the correct value and if
    such a build does not exist, report an empty string ("").</td>
 </tr>
</table>

### 3.2.3\. Intent Compatibility

#### 3.2.3.1\. Core Application Intents

Android intents allow application components to request functionality from
other Android components. The Android upstream project includes a list of
applications considered core Android applications, which implements several
intent patterns to perform common actions. The core Android applications are:

*   Desk Clock
*   Browser
*   Calendar
*   Contacts
*   Gallery
*   GlobalSearch
*   Launcher
*   Music
*   Settings


Device implementations MUST include the core Android applications as
appropriate or a component implementing the same intent patterns defined by
all the Activity or Service components of these core Android applications
exposed to other applications, implicitly or explicitly, through the
`android:exported` attribute.

#### 3.2.3.2\. Intent Resolution

As Android is an extensible platform, device implementations MUST allow each
intent pattern referenced in [section 3.2.3.1](#3_2_3_1_core_application_intents) to be overridden by third-party
applications. The upstream Android open source implementation allows this by
default; device implementers MUST NOT attach special privileges to system
applications' use of these intent patterns, or prevent third-party applications
from binding to and assuming control of these patterns. This prohibition
specifically includes but is not limited to disabling the “Chooser” user
interface that allows the user to select between multiple applications that all
handle the same intent pattern.

Device implementations MUST provide a user interface for users to modify the
default activity for intents.

However, device implementations MAY provide default activities for specific URI
patterns (e.g. http://play.google.com) when the default activity provides a
more specific attribute for the data URI. For example, an intent filter pattern
specifying the data URI “http://www.android.com” is more specific than the
browser's core intent pattern for “http://”.

Android also includes a mechanism for third-party apps to declare an
authoritative default [app linking behavior](https://developer.android.com/training/app-links)
for certain types of web URI intents. When such authoritative declarations are
defined in an app's intent filter patterns, device implementations:

*   MUST attempt to validate any intent filters by performing the validation
steps defined in the [Digital Asset Links specification](https://developers.google.com/digital-asset-links)
as implemented by the Package Manager in the upstream Android Open Source
Project.
*   MUST attempt validation of the intent filters during the installation of
the application and set all successfully validated UIR intent filters as
default app handlers for their UIRs.
*   MAY set specific URI intent filters as default app handlers for their URIs,
if they are successfully verified but other candidate URI filters fail
verification. If a device implementation does this, it MUST provide the
user appropriate per-URI pattern overrides in the settings menu.
*   MUST provide the user with per-app App Links controls in Settings as
follows:
    *   The user MUST be able to override holistically the default app links
    behavior for an app to be: always open, always ask, or never open,
    which must apply to all candidate URI intent filters equally.
    *   The user MUST be able to see a list of the candidate URI intent filters.
    *   The device implementation MAY provide the user with the ability to
    override specific candidate URI intent filters that were successfully
    verified, on a per-intent filter basis.
    *   The device implementation MUST provide users with the ability to view
    and override specific candidate URI intent filters if the device
    implementation lets some candidate URI intent filters succeed
    verification while some others can fail.

#### 3.2.3.3\. Intent Namespaces

Device implementations MUST NOT include any Android component that honors any
new intent or broadcast intent patterns using an ACTION, CATEGORY, or other key
string in the android.* or com.android.* namespace. Device implementers MUST
NOT include any Android components that honor any new intent or broadcast
intent patterns using an ACTION, CATEGORY, or other key string in a package
space belonging to another organization. Device implementers MUST NOT alter or
extend any of the intent patterns used by the core apps listed in
[section 3.2.3.1](#3_2_3_1_core_application_intents). Device implementations MAY
include intent patterns using namespaces clearly and obviously associated with
their own organization. This prohibition is analogous to that specified for Java
language classes in [section 3.6](#3_6_api_namespaces).

#### 3.2.3.4\. Broadcast Intents

Third-party applications rely on the platform to broadcast certain intents to
notify them of changes in the hardware or software environment.
Android-compatible devices MUST broadcast the public broadcast intents in
response to appropriate system events. Broadcast intents are described in the
SDK documentation.

#### 3.2.3.5\. Default App Settings

Android includes settings that provide users an easy way to select their
default applications, for example for Home screen or SMS. Where it makes sense,
device implementations MUST provide a similar settings menu and be compatible
with the intent filter pattern and API methods described in the SDK
documentation as below.

Device implementations:

*   MUST honor the
[android.settings.HOME_SETTINGS](http://developer.android.com/reference/android/provider/Settings.html#ACTION_HOME_SETTINGS)
intent to show a default app settings menu for Home Screen, if the device
implementation reports android.software.home_screen.
*   MUST provide a settings menu that will call the
[android.provider.Telephony.ACTION_CHANGE_DEFAULT](http://developer.android.com/reference/android/provider/Telephony.Sms.Intents.html)
intent to show a dialog to change the default SMS application, if the
device implementation reports android.hardware.telephony.
*   MUST honor the
[android.settings.NFC_PAYMENT_SETTINGS](http://developer.android.com/reference/android/provider/Settings.html#ACTION_NFC_PAYMENT_SETTINGS)
intent to show a default app settings menu for Tap and Pay, if the device
implementation reports android.hardware.nfc.hce.
*   MUST honor the [android.telecom.action.CHANGE_DEFAULT_DIALER](https://developer.android.com/reference/android/telecom/TelecomManager.html#ACTION_CHANGE_DEFAULT_DIALER)
intent to show a dialog to allow the user to change the default Phone application, if the
device implementation reports `android.hardware.telephony`.
*   MUST honor the [android.settings.ACTION_VOICE_INPUT_SETTINGS](https://developer.android.com/reference/android/provider/Settings.html#ACTION_VOICE_INPUT_SETTINGS)
    intent when the device supports the VoiceInteractionService and show a
    default app settings menu for voice input and assist.