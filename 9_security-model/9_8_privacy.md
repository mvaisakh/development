## 9.8\. Privacy

If the device implements functionality in the system that captures the contents
displayed on the screen and/or records the audio stream played on the device,
it MUST continuously notify the user whenever this functionality is enabled and
actively capturing/recording.

If a device implementation has a mechanism that routes network data traffic
through a proxy server or VPN gateway by default (for example, preloading a VPN
service with android.permission.CONTROL_VPN granted), the device implementation
MUST ask for the user's consent before enabling that mechanism.

Device implementations MUST ship with an empty user-added Certificate Authority
(CA) store, and MUST preinstall the same root certificates for the system-trusted
CA store as [provided](https://source.android.com/security/overview/app-security.html#certificate-authorities)
in the upstream Android Open Source Project.

If a device implementation has a USB port with USB peripheral mode support, it
MUST present a user interface asking for the user's consent before allowing
access to the contents of the shared storage over the USB port.