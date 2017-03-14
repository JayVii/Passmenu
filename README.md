# Passmenu

custom 1-line script to ease the usage of "pass" passwordmanager.

### Requirements
* [Pass](http://www.passwordstore.org/)
* [GnuPG](https://www.gnupg.org/)
* [Dmenu](http://tools.suckless.org/dmenu/)
* [Pinentry](https://www.gnupg.org/related_software/pinentry/index.html)
* [xclip](http://sourceforge.net/projects/xclip/)

You need to set up [pass](https://wiki.archlinux.org/index.php/Pass) & [GPG](https://wiki.archlinux.org/index.php/GnuPG) correctly.
It's a good idea to bind this script to a hotkey.

### How it works
Pipes all your stored passwords (pass -ls) into dmenu.
Gets rid of all leading symbols (|-- and `--).
Saves the password for 45 seconds in your clipboard.

Just run the script, type the first letters of your container (eg: twitter.com) and press enter/return.
Pinetry will promt you for your gpg-password, afterwards.
The container's password will remain in your clipboard for 45 seconds.
```
pass show -c $(pass ls | sed "s/|--//g" | sed "s/\`--//g" | sed "s/Password Store//g" | dmenu -b -p Passmenu)
```
