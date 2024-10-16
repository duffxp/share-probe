### Base

STB Model: **apollo_p7**
```
ro.product.system.model]: [apollo_p7]
[ro.soc.model]: [H618]
```

You can download all the files and the videos demonstrating the behaviors in the link: https://we.tl/t-53dMUTDTy9

---
### Description

- We have 3x TS file with different audio codecs: `ac3`, `mp2` and `aac`;
- For this test, we used [AndroidX Media3 by Google](https://github.com/androidx/media), simulating exactly our scenario (we use this same AndroidX project in our applications);
- For test this source in multicast, we used `FFmpeg` with this command line:
```
ffmpeg -re -stream_loop -1 -i 'bbb-aac.mp4' -c copy -f mpegts 'udp:224.10.10.1:1234?localaddr=192.168.115.254'
```
---
### Resume


- The TS file with `aac` codec worked normally (video and audio).
  - You can check the ADB logs in: [aac](aac.txt)
- The stream with `mp2` codec played the video very well, but it did not play the audio. The message "there is no codec to support the audio track" appears.
  - You can check the ADB logs in: [mp2](mp2.txt)
- The stream with `ac3`, despite not showing the unsupported codec message, simply does not play the video or the audio. The image is completely frozen.
  - You can check the ADB logs in: [ac3](ac3.txt)

---
### Note

About the test with `aac` codec, the video looks strange at times, displaying green composites and frame breaks, apparently.

Please, check it out in [video-sample-a](video-sample-a.jpeg), [video-sample-b](video-sample-b.jpg) and [video-sample-c](video-sample-c.jpg)
