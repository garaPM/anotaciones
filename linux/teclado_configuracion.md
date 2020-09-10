# Configuración del teclado

Change keyboard configuration in console – /dev/blog

To **temporarily** change a console’s keyboard mapping there’s [loadkeys](http://linuxmanpages.net/manpages/fedora21/man1/loadkeys.1.html), a little user space program that allows you to alter the kernel’s keyboard mapping.  
Loading the very handy [US International keyboard layout](https://en.wikipedia.org/wiki/British_and_American_keyboards), use

To list the currently used keyboard layout or all available keyboard layouts, [localectl](https://www.freedesktop.org/software/systemd/man/localectl.html) can be used

|     |     |
| --- | --- |
| 1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6 | `System Locale: LANG=en_US.UTF-8`<br><br>`VC Keymap: us-altgr-intl`<br><br>`X11 Layout: us`<br><br>`[...]` |

If `localectl` is not available, keyboard mapping files are usually found at `/lib/kbd/keymaps/xkb/` (e.g. Fedora) or `/usr/share/kbd/keymaps/` (e.g. [Arch Linux](https://wiki.archlinux.org/index.php/Keyboard_configuration_in_console)).

To **permanently** change the default keyboard layout system-wide, alter `/etc/vconsole` accordingly

|     |     |
| --- | --- |/etc/vconsole
| 1<br><br>2 | `KEYMAP="us-altgr-intl"`<br><br>`FONT="eurlatgr"` |