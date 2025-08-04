Assuming a standard Ubuntu 20.04 sound topology (aka ALSA+PulseAudio mixers), use the following commands:

Mute:

```sh
amixer -D pulse set Capture nocap
```

Unmute:
```sh
amixer -D pulse set Capture cap
```

In `cap` and `nocap`, `cap` refers to `Capture` aka sound input.

This can be used to implement a systemwide "push to talk" functionality that doesn't need to be supported by each individual application, like Teams.

To mute output instead, use something like `amixer -D pulse set Master <'mute'/'unmute'>`

