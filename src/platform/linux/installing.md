# Встановлення та оновлення ANKI на Linux

<!-- toc -->

## Вимоги

Для пакетної версії потрібна остання 64-розрядна версія Intel/AMD Linux із glibc і загальні бібліотеки, такі як libwayland-client і systemd. Якщо ви використовуєте іншу архітектуру (наприклад, ARM/AArch64) або базовий дистрибутив Linux, ви не зможете скористатися пакетною версією, але зможете скористатися [Python wheels](https://betas.ankiweb.net/#via-pypipip).

Для Debian і похідних, таких як Ubuntu і [Chromebook з увімкненою ОС Linux](https://support.google.com/chromebook/answer/9145439?), будь ласка, скористайтеся наведеним нижче перед інсталяцією:

```shell
sudo apt install libxcb-xinerama0 libxcb-cursor0 libnss3
```

Якщо Anki не запускається після встановлення, можливо, у вас [відсутні інші бібліотеки](./missing-libraries.md).

Якщо ви використовуєте Ubuntu 24.04 і Anki не запускається, перегляньте [цю тему] (https://forums.ankiweb.net/t/issues-running-on-ubuntu-24-04/40974).

Система збірки Anki підтримує лише glibc, тому дистрибутиви на основі musl наразі не підтримуються.

## Installing

To install Anki:

1. Download Anki from <https://apps.ankiweb.net> to your Downloads folder. See the next section
   for how to choose between -qt5 and -qt6.
2. If zstd is not already installed on your system, you'll need to install it (e.g `sudo apt install zstd`).
3. Open a terminal and run the following commands, replacing the filename as appropriate.

```shell
tar xaf Downloads/anki-2XXX-linux-qt6.tar.zst
cd anki-2XXX-linux-qt6
sudo ./install.sh
```

On some Linux systems, you may need to use `tar xaf --use-compress-program=unzstd`.

4. You can then start Anki by typing 'anki' and hitting enter. If you encounter
   any issues, please see the links on the left.

## Qt5 vs. Qt6

Recent Anki versions come in separate Qt5 and Qt6 variants. The Qt6 version
is recommended for most users.

Advantages of the Qt6 version:

- Compatibility with recent glibc versions (fixes [blank screens on recent distros](./blank-window.md)).
- Better HiDPI support.
- Better Wayland support.
- Various bugfixes, including things like better support for less common languages.
- Security updates. Support for the Qt5 library was discontinued in Nov 2020,
  meaning that any security flaws discovered since then will remain unfixed.

Disadvantages of the Qt6 version include:

- Some add-ons currently only work with the Qt5 version.

## Upgrading

If you were running Anki from a .deb/.rpm/etc in the past, please make
sure to remove the system version before installing the package
provided here.

If you're upgrading from a previous package, simply repeat the
installation steps to upgrade to the latest version. Your user data
will be preserved.

If you wish to downgrade to a previous version, please make sure you
[downgrade first](http://changes.ankiweb.net).

## Add-on Compatibility

Some add-ons may not always work with the latest Anki release. If you upgrade to
the latest Anki version and find an add-on you cannot live without stops working,
you can download older Anki versions from the [releases page](https://github.com/ankitects/anki/releases).

## Problems

If you encounter any issues when installing or starting Anki, please see the
following pages:

- [Missing Libraries](missing-libraries.md)
- [Display Issues](display-issues.md)
- [Blank Main Window](blank-window.md)
- [Linux Distro Packages](distro-packages.md)
- [Incorrect GTK Theme](gtk-theme.md)
- [Wayland](wayland.md)
- [Input Methods](input-methods.md)
