# List of bugs or unexpected behaviours I encountered when using Barrier

### Wayland / Ubuntu 22.04.1 mouse cursor does not move to another machine

Barrier currently suffers from a bug when running under Wayland: https://github.com/debauchee/barrier/issues/1659

Ubuntu 22.04.1 by default launches the GUI in Wayland mode. The solution (for now) is to switch back to X.org (or, for some inexplicable reason, launch Firefox).

### Wayland expects TLS between machines

The way to solve this is to give the relevant machines a TLS certificate each so that they can communicate, or disable TLS.

### Barrier hostname matters

This applies to the hostname configured in the small "Configuration" pop-up window. It **must** match what your hostname/machine name is in the drag-and-drop machine layout diagram, otherwise barrier will not function properly.

The same applies to each client machine. Basically, pick one (host-/machine-)name for each machine, and stick with it when configuring the application.
