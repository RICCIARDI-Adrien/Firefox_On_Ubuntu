# How to install binary Firefox on Ubuntu

Ubuntu 22.04 has removed the Firefox `deb` package that was maintained by Canonical and replaced it by a Snap package.
Here is how to replace the Firefox Ubuntu Snap package by the Mozilla-provided binary.

This procedure has been tested on **Xubuntu 22.04**.

## Download the official Firefox binary

Download the latest Firefox version from the [official website](https://www.mozilla.org/fr/firefox/all/#product-desktop-release).
You will get a compressed `tar` archive named like `firefox-99.0.1.tar.bz2`.

## Remove the Snap version of Firefox

This will preserve your existing Firefox profile(s) located in `~/.mozilla/firefox`.

```
sudo snap remove firefox
```

## Install the binary version of Firefox

1. Make sure that you have the needed permissions to write to the `/opt` directory. If not, use a command like `sudo chmod 777 /opt` to give the needed permissions.
2. Extract the downloaded archive to `/opt` (adapt the archive name to the one you downloaded) : `tar -xf firefox-99.0.1.tar.bz2 -C /opt`.
3. Create a symbolic link to the Firefox binary : `sudo ln -s /opt/firefox/firefox /usr/bin/`.

## Set binary Firefox as the default web browser

### For Xfce desktop

1. From the menu, open `Settings -> Default applications`.
2. In the `Web Browser` section, select `Other...` from the drop-down menu and type `/opt/firefox/firefox`.

## Switch to your existing profile

By default, the binary version of Firefox creates a new empty profile.
Follow these instructions to get back to your current profile with all your bookmarks, extensions, history and so on.

1. Start Firefox (you can access it from the main menu by clicking on the `Web Browser` application).
2. In the address bar, type `about:profiles` to display all available profiles.
3. Set the profile you want as default (the profile you were using with the old `deb` Firefox is usually called `default`).
4. Close Firefox.
5. **OPTIONAL** : you can now safely delete the empty profile created by Firefox. Restart Firefox, go to `about:profiles` page and delete the profile called `default-release`.

See the [official wiki](https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles#w_manage-profiles-when-firefox-is-open) for more information about profiles.
