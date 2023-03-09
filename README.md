install-jdk8-on-steam-deck
=========================

<!--ts-->
* Credits(#credits)
* [How it works](#how-it-works)
* [Usage](#usage)

<!--te-->

Credits
============
All credits go to ![BlackCorsair](https://github.com/BlackCorsair) for his wonderful install-jdk-on-steam script. This is merely a modified version of his script to instead install JDK 8 instead of JDK 17.

How it works
============
By default, the SteamDeck has a [read-only][1] immutable OS file system, which means that you can't simply
install anything using the `pacman` package manager that comes with the OS (arch linux), since it would modify
the OS file system.

So in order to install anything outside the Software Center (which installs programs in a way that doesn't affect
the OS by using [flatpak][2]), you have to modify things in you *home* directory, which shouldn't mess up with the OS
and break the system.

Taking this into account, the script located in the `scripts` directory of this repository will:
* Download the official oracle JDK 8 compressed file into your **home** directory, more specifically into `~/.local/jdk`
* Exec a checksum of the file using the official sha256 checksum
* Extract the file into `~/.local/jdk/jdk8u362-b09`
* Add some environment variables to your `~/.bashrc`, so your programs / scripts know where `java` is installed.
    The variables are:
    * JAVA_HOME: which points to the `~/.local/jdk/jdk8u362-b09`
    * PATH: which adds the `bin` directory located in the JAVA_HOME, so every executable is available for you to run

With this, you will have a *local* installation of java and even better, you can install multiple versions and then point
to the one you need.

This script only works for the jdk-8. For the excellent jdk-17 version, go here: https://github.com/BlackCorsair/install-jdk-on-steam-deck

Usage
=====
```bash
git clone https://github.com/ipkpjersi/install-jdk8-on-steam-deck.git
./install-jdk8-on-steam-deck/scripts/install-jdk8.sh
```

[1]: https://partner.steamgames.com/doc/steamdeck/faq
[2]: https://www.flatpak.org/
