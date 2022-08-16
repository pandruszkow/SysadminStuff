# Logitech C920 Pro HD

This webcam is a bit of an odd duck. It's advertised as supporting up to 1080p @ 30fps, but under Linux it seemingly only supports 1080p at 5fps? What gives?

## TL;DR
Use the following settings for the following apps:
| App | Setting|
|-----|--------|
|OBS| YV12 (tested on Ubuntu 20.04, OBS 25.0.3)|
|Microsoft Teams for Linux desktop app (v1.5)|Only low-res mode is supported. Use it in Chrome instead to access higher resolutions.|

## More detailed explanation

Turns out, this webcam effectively has 2 (3?) modes that can be used to access the video stream:

* the low-resolution mode - what most applications seem to use on Linux unless told otherwise - this hits the full 30fps.

* the native H264 streaming mode - that's right, the camera will internally encode what's coming out of the sensor into H264 and stream that down the USB wire. This is handy if you want (or just don't mind) having the video stream pre-encoded, **but this seems to be unavailable in the desktop Microsoft Teams for Linux app** (as of v1.5 DEB64 on Ubuntu 20.04).

* the emulated decompressed-reencoded high-resolution mode - the OS will de-compress the H264 stream and convert it to a normal webcam video stream behind the scenes, then feed that to the respective applications requesting the video stream.

  * This can be slow if you pick a different colour space to the one from the original video stream, so **you must select the right "video format" out of YV12, YU12, and BGR3**. I don't know what the differences are between the three of these, but they seem to work just fine in OBS.

  * Selecting `YUYV 4:2:2` in OBS will absolutely obliterate the framerate and turn it into something closer to 5fps (or lower). I'm guessing this is the slower emulated mode.
