---
layout:      post
title:       "Installing multimon-ng and qtmake on Ubuntu 17.10"
category:    Posix
tags:        [qmake, qt5, ubuntu, multimon-ng, "amateur radio"]
---

I needed a copy of **qmake** to install **multimon-ng** on Ubuntu 17.10. Unfortunately this turned out to not be as easy as *sudo apt install qmake*! So for the next time I need multimon-ng on a different posix system this is what I ended up doing:

~~~shell
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
~~~
