# Microsoft Teams for Linux desktop app

## The issues

The app generally works OK, but it has a number of annoying problems:

* Slow as molasses - both to launch, to react to user input, and to "lazy load" the Calendar tab (which is the only thing I ever want, because I primarily use Teams to dial into video meetings.
* No support for webcam backgrounds (not even the blur feature)
* No support for high-resolution modes on the Logitech C920

The latter issue is why I decided to do away with the "native" Electron app and switch to the Chrome(ium) version instead. Once the initial login is done, it really seems like Teams in-browser does better on each of these counts - it's faster, it supports some webcam backgrounds. High-resolution webcam modes work fine, but there's some screen tearing - that's just Linux for you.

## The solution / current setup

We're going to be creating an "app" shortcut from Chrome for more convenient access to Teams in-browser, and to make it behave as if it was an integrated desktop app.

1. Open Chrome/Chromium and log into your Microsoft account
2. Navigate to the main page of Teams (this is so that we can get a "clean" shortcut URL)
3. Click the Chrome three-dot menu button in the upper right-hand corner
4. Select `More tools` -> `Create shortcut...`
5. Enter "Microsoft Teams" as the shortcut name and tick "Open as window" (this will turn it into a standalone "app")
6. Click "Create"

Now you have created a Microsoft Teams launcher that will embed the Teams browser app into a Chrome(ium) window once launched. I recommend pinning it to the taskbar or dragging it to the desktop, or something like that for easy access.

If you have more than one camera connected to your computer (say, because you are on a laptop with an internal camera and you connected an external camera like the Logitech C920 for better picture quality), you may want to tweak your camera settings so that the meeting starts with the right camera pre-selected:

1. Open Chrome(ium)
2. Navigate to `chrome://settings/content/camera?search=camera`
3. From the dropdown, select the camera you prefer to use for video calling
