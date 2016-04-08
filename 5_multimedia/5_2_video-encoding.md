## 5.2\. Video Encoding

<div class="note">

Video codecs are optional for Android Watch device implementations.

</div>

Android device implementations with H.263 encoders MUST support Baseline
Profile Level 45.

Android device implementations with H.264 codec support MUST support Baseline
Profile Level 3 and the following SD (Standard Definition) video encoding
profiles and SHOULD support Main Profile Level 4 and the following HD (High
Definition) video encoding profiles. Android Television devices are STRONGLY
RECOMMENDED to encode HD 1080p video at 30 fps.

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
    <td>20 fps</td>
    <td>30 fps</td>
    <td>30 fps</td>
    <td>30 fps</td>
 </tr>
 <tr>
    <th>Video bitrate</th>
    <td>384 Kbps</td>
    <td>2 Mbps</td>
    <td>4 Mbps</td>
    <td>10 Mbps</td>
 </tr>
</table>


<p class="table_footnote">1 When supported by hardware, but STRONGLY RECOMMENDED
for Android Television devices.</p>


Android device implementations with VP8 codec support MUST support the SD video encoding profiles and SHOULD support the following HD (High Definition) video encoding profiles.

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
    <td>30 fps</td>
    <td>30 fps</td>
 </tr>
 <tr>
    <th>Video bitrate</th>
    <td>800 Kbps </td>
    <td>2 Mbps</td>
    <td>4 Mbps</td>
    <td>10 Mbps</td>
 </tr>
</table>

<p class="table_footnote">1 When supported by hardware.</p>


