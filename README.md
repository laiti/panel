# panel
My setup for a dashboard. Probably not usable as-is but perhaps it can work as an inspiration or a guide.

## Tools
- X11
- [rxvt](https://rxvt.net)
- [tty-clock](https://github.com/xorg62/tty-clock)
- [Grafana](https://grafana.com/)
- [pricedisplay](https://github.com/YukiNeko-hime/pricedisplay/)
- [ympd](https://github.com/SuperBFG7/ympd) - with [custom CSS](https://github.com/laiti/ympd)
- [x11vnc](https://github.com/LibVNC/x11vnc)
- [qrencode](https://fukuchi.org/works/qrencode/)

## How to install
1. Checkout the repository to /opt/panel
2. Install systemd file
3. Install the software mentioned in Tools section
4. `systemctl start panel.service`

## How it works
The systemd service specified in `systemd/panel.service` starts up a X11 session in vt7. So in other words it expects your system to have no other X11 services enabled.

Instead of starting a window manager, it fires up borderless chromium and rxvt windows, displaying all kinds of data. It also starts x11vnc server if you need to do some debugging or log in to a service.

## What are the rest of the directories?

- `bin` contains the scripts we run. `panel` as the main script, calling the rest.
- `etc` should contain only one file: `etc/wifi`. It is used for generating the QR code for guest wifi.
- `Xresources` contains rxvt configurations for the terminal windows.