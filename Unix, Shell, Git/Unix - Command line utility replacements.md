Legacy Unix utilities have awful command line APIs (or simply unconventional ones). Some are worth replacing.

# grep

Replace with Ripgrep

# find

Replace with [fd](https://github.com/sharkdp/fd)

# ls

Replace with exa

# git

Not technically a legacy utility, but the usage model is very complex. It's far better to use an extensive set of aliases, [such as mine](https://github.com/pandruszkow/gitconfigure)

# bash

Replace with ZSH. Replacement instructions TODO.

# ncdu

Replace with [gdu](https://github.com/dundee/gdu). Bonus: this is a statically-compiled Go application, so it can be deployed in a single binary on servers with outdated OS versions.
