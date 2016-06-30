## 5.3\. Video Decoding

<div class="note">

Video codecs are optional for Android Watch device implementations.

</div>

Device implementations MUST support dynamic video resolution and frame rate
switching through the standard Android APIs within the same stream for all VP8,
VP9, H.264, and H.265 codecs in real time and up to the maximum resolution
supported by each codec on the device.

Android device implementations with H.263 decoders MUST support Baseline Profile Level 30.

Android device implementations with MPEG-4 decoders MUST support Simple Profile Level 3.

### 5.3.1\. H.264

Android device implementations with H.264 decoders MUST support Main Profile
Level 3.1 and the following SD video decoding profiles and SHOULD support the
HD decoding profiles. Android Television devices MUST support High Profile
Level 4.2 and the HD 1080p decoding profile.

<table>
 <tr>
    <th></th>
    <th>SD (Low quality)</th>
    <th>SD (High quality)</th>
    <th>HD 720p<sup>1</sup></th>
    <th>HD 1080p<sup>1</sup></th>
 </tr>
 <tr>
    <th>Video resolution</th>
    <td>320 x 240 px</td>
    <td>720 x 480 px</td>
    <td>1280 x 720 px</td>
    <td>1920 x 1080 px</td>
 </tr>
 <tr>
    <th>Video frame rate</th>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>60 fps</td>
    <td>30 fps / 60 fps<sup>2</sup></td>
 </tr>
 <tr>
    <th>Video bitrate</th>
    <td>800 Kbps </td>
    <td>2 Mbps</td>
    <td>8 Mbps</td>
    <td>20 Mbps</td>
 </tr>
</table>


<p class="table_footnote">1 REQUIRED for when the height as reported by the
Display.getSupportedModes() method is equal or greater than the video resolution.</p>

<p class="table_footnote">2 REQUIRED for Android Television device
implementations.</p>

### 5.3.2\. H.265

Android device implementations, when supporting H.265 codec as described in
[section 5.1.3](#5_1_3_video_codecs), MUST support the Main Profile Level 3
Main tier and the following SD video decoding profiles and SHOULD support the
HD decoding profiles. Android Television devices MUST support the Main Profile
Level 4.1 Main tier and the HD 1080p decoding profile and SHOULD support Main10
Level 5 Main Tier profile and the UHD decoding profile.

<table>
 <tr>
    <th></th>
    <th>SD (Low quality)</th>
    <th>SD (High quality)</th>
    <th>HD 720p<sup>1</sup></th>
    <th>HD 1080p<sup>1</sup></th>
    <th>UHD<sup>2</sup></th>
 </tr>
 <tr>
    <th>Video resolution</th>
    <td>352 x 288 px</td>
    <td>640 x 360 px</td>
    <td>1280 x 720 px</td>
    <td>1920 x 1080 px</td>
    <td>3840 x 2160 px</td>
 </tr>
 <tr>
    <th>Video frame rate</th>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>60 fps<sup>2</sup></td>
    <td>60 fps</td>
 </tr>
 <tr>
    <th>Video bitrate</th>
    <td>600 Kbps </td>
    <td>1.6 Mbps</td>
    <td>4 Mbps</td>
    <td>10 Mbps</td>
    <td>20 Mbps</td>
 </tr>
</table>


<p class="table_footnote">1 Required for Android Television device
implementations, but for other type of devices only when supported by hardware.
</p>

<p class="table_footnote">2 STRONGLY RECOMMENDED for existing Android Television
device implementations when supported by hardware.</p>


### 5.3.3\. VP8

Android device implementations, when supporting VP8 codec as described in
[section 5.1.3](#5_1_3_video_codecs), MUST support the following SD decoding
profiles and SHOULD support the HD decoding profiles. Android Television
devices MUST support the HD 1080p decoding profile.

<table>
 <tr>
    <th></th>
    <th>SD (Low quality)</th>
    <th>SD (High quality)</th>
    <th>HD 720p<sup>1</sup></th>
    <th>HD 1080p<sup>1</sup></th>
 </tr>
 <tr>
    <th>Video resolution</th>
    <td>320 x 180 px</td>
    <td>640 x 360 px</td>
    <td>1280 x 720 px</td>
    <td>1920 x 1080 px</td>
 </tr>
 <tr>
    <th>Video frame rate</th>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>30 fps / 60 fps<sup>2</sup></td>
    <td>30 / 60 fps<sup>2</sup></td>
 </tr>
 <tr>
    <th>Video bitrate</th>
    <td>800 Kbps </td>
    <td>2 Mbps</td>
    <td>8 Mbps</td>
    <td>20 Mbps</td>
 </tr>
</table>

<p class="table_footnote">1 REQUIRED for when the height as reported by the
Display.getSupportedModes() method is equal or greater than the video resolution.</p>

<p class="table_footnote">2 REQUIRED for Android Television device
implementations.</p>

### 5.3.4\. VP9

Android device implementations, when supporting VP9 codec as described in
[section 5.1.3](#5_1_3_video_codecs), MUST support the following SD video
decoding profiles and SHOULD support the HD decoding profiles. Android Television
devices are STRONGLY RECOMMENDED to support the HD 1080p decoding profile and
SHOULD support the UHD decoding profile. When the UHD video decoding profile is
supported, it MUST support 8-bit color depth and SHOULD support VP9 Profile 2 (10-bit).

<table>
 <tr>
    <th></th>
    <th>SD (Low quality)</th>
    <th>SD (High quality)</th>
    <th>HD 720p<sup>1</sup></th>
    <th>HD 1080p<sup>2</sup></th>
    <th>UHD<sup>2</sup></th>
 </tr>
 <tr>
    <th>Video resolution</th>
    <td>320 x 180 px</td>
    <td>640 x 360 px</td>
    <td>1280 x 720 px</td>
    <td>1920 x 1080 px</td>
    <td>3840 x 2160 px</td>
 </tr>
 <tr>
    <th>Video frame rate</th>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>60 fps</td>
    <td>60 fps</td>
 </tr>
 <tr>
    <th>Video bitrate</th>
    <td>600 Kbps</td>
    <td>1.6 Mbps</td>
    <td>4 Mbps</td>
    <td>5 Mbps</td>
    <td>20 Mbps</td>
 </tr>
</table>


<p class="table_footnote">1 Required for Android Television device
implementations, but for other type of devices only when supported by hardware.
</p>

<p class="table_footnote">2 STRONGLY RECOMMENDED for existing Android Television
device implementations when supported by hardware.</p>
