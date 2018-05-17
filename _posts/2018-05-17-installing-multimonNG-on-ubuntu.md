---
layout:      post
title:       "Installing MultimonNG (and QMake) on Ubuntu 17.10"
category:    Posix
tags:        [QMake, Qt5, Ubuntu, MultimonNG, "Amateur Radio"]
image:
  thumbnail: /images/multimonNG.png
---

I needed a copy of **QMake** to install **MultimonNG** on Ubuntu
17.10. QMake is a component of the Qt Framework. It is a utility to
automate the generation of makefiles. The generated makefile is then
used to build a final application (in this case MultimonNG).

Unfortunately, getting a copy of QMake proved to be *not quite* as
easy as *sudo apt install qmake*! So for the next time I need
**MultimonNG** on a different Posix system this is what I ended up
doing:-

## Installation

```sh
git clone --depth=1 https://github.com/EliasOenal/multimon-ng.git
cd multimon-ng
sudo apt install qt5-qmake
export QT SELECT=qt5
sudo ln /usr/lib/x86_64-linux-gnu/qt5/bin/qmake /usr/bin/qmake
qmake -v
# => QMake version 3.1
# => Using Qt version 5.9.1 in /usr/lib/x86_64-linux-gnu
mkdir build && cd build
qmake ../multimon-ng.pro PREFIX=/usr/local
sudo apt install libpulse-dev libx11-dev
make
sudo make install
multimon-ng -h
# => multimon-ng 1.1.5
```
<figure class="align-center">
  <a href="https://github.com/EliasOenal/multimon-ng"><img src="{{ '/images/multimonNG.png' | absolute_url }}" alt="MultimonNG"></a>
  <figcaption>MultimonNG</figcaption>
</figure>

# Testing

The command I used to test MultimonNG:-

```sh
multimon-ng example/ufsk1200.raw -t raw
```

MultimonNG can be found [on Github](https://github.com/EliasOenal/multimon-ng)

Now... What was it I needed MultimonNG for again?

