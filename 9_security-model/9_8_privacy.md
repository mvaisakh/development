## 9.8\. Privacy

If the device implements functionality in the system that captures the contents
displayed on the screen and/or records the audio stream played on the device,
it MUST continuously notify the user whenever this functionality is enabled and
actively capturing/recording.

If a device implementation has a mechanism that routes network data traffic
through a proxy server or VPN gateway by default (for example, preloading a VPN
service with android.permission.CONTROL_VPN granted), the device implementation
MUST ask for the user's consent before enabling that mechanism.

When devices are routed through a VPN, or a user root CA is installed, the
implementation MUST display a warning indicating the network traffic may be
monitored to the user.

If a device implementation has a USB port with USB peripheral mode support, it
MUST present a user interface asking for the user's consent before allowing
access to the contents of the shared storage over the USB port.

