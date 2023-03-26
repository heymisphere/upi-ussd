# Pe

Pe is a [libadwaita](https://https://gitlab.gnome.org/GNOME/libadwaita) and [ModemManager](https://www.freedesktop.org/wiki/Software/ModemManager/) based UPI client for Linux Desktops and Linux Mobile phones, written in Python.

This client utilises ```*99#``` service publically available on Airtel, Vi, BSNL (not Jio), provided by NCPI.

As it uses the ```*99#``` USSD service, it requires a modem connected. While linux phones already have built-in modem, some laptops also have inbuilt WAN or SIM ports. You may also connect Linux-compatible modems to your computer.

It is prone to failing, because of the nature of USSD service, and network strengths.

The developer is not reponsible for any loss of money or any complications. So, try on your own risk.

Pe provides two binaries ```pe``` and ```pe-cli```. By default, launnching the app through flatpak would launch ‘pe’ which is the graphical app. But you can optionally run the ```pe-cli``` binary, which provides a command line interface.

As the app is currently in development, I have not implemented a lot of error handling. The app would not even start in absence of modem, if built with normal profile. There exists a testing profile, which does a dry run, and does not utilise any modem, and is there only for testing the GUI.

ModemManager service is already installed and enabled by default in distros like Ubuntu, Fedora. But, it may not be installed in other distros. You need to install ModemManager and enable it in your distro (that doesn't always require systemd, if you are using an init system other than systemd, you can still launch the service through your respective init system).

It was GTK4/Libadwaita learning project for me, so I have fairly documented the GUI code.

The GUI code is separated from backend code. So, in case in future, we come forward to use some backend other than USSD, just utils.py can be replaced to provide the same functions.

The most easy way to run this app, is using GNOME Builder, or using Flatpak extension for VS Code or VSCodium. I have provided two flatpak manifests, one for normal profile and one for testing profile.

Though you can also build the project locally, without Flatpak by:

```
meson build -Dprofile=testing
cd build
sudo meson install
```

(testing mode)

```meson build 
cd build
sudo meson install
```

(normal mode)