auto-xflux
==========

Inputless xflux daemon that geocodes based on your external IP address.

This requires working systemd instance and X server for the user executing xflux. It requires an
Internet connection to already be established and assumes that the following services are online:

- [icanhazip.com]
- [geocodeip.com]

This also obviously requires [xflux](https://justgetflux.com/linux.html) (to be accessible in $PATH).

## Modification
- Only acquire IPv4 address.
- Fix bug on negative lat/long
- Modified for Debian Jessie KDE
  - Use /bin/bash instead of /bin/sh in order to support Debian KDE

## Installation

### Arch Linux

Installed the AUR package, [auto-xflux](aur.archlinux.org/packages/auto-xflux). The PKGBUILD can be viewed
[here](https://github.com/jamesan/aur-pkgs/blob/master/auto-xflux/PKGBUILD).

### Other

Installed by downloading the files in this repository and running:

    make [DESTDIR=DIRECTORY] install

and uninstalled by runnning:

    make [DESTDIR=DIRECTORY] uninstall

DESTDIR is included for installing to a non-root (/) location.

#### Debian Jessie KDE
- add ```/usr/bin/auto-xflux``` to startup scripts in order to start after boot
- add ```kill $(ps aU $USER | pgrep 'xflux' | awk '{print $1}')``` to shutdown scripts to kill xflux after logout
- Replace ```exec `which xflux```` by /path/to/xflux if the script does not work.
