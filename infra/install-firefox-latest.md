# Installing the latest Firefox

Firefox is a little odd, at least on Debian, because only the extended support release is available in the main repos. One
easy fix, though, is to install it manually to your home directory!

Here's what I do to install it:

```bash
# Download firefox
curl -L "https://download.mozilla.org/?product=firefox-latest&os=linux64&lang=en-US" -o firefox-latest.tar.bz2

# Untar it
tar xvf firefox-latest.tar.bz2 -C $HOME/.local/lib/
```

Now you need a `.desktop` file to make sure it shows up in your launcher. We'll put that into `~/.local/share/applications/firefox.desktop`:

```ini
[Desktop Entry]
Name=Firefox
Comment=Browse the World Wide Web
GenericName=Web Browser
X-GNOME-FullName=Firefox Web Browser
Exec=/home/nalanj/.local/lib/firefox/firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox-esr
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;
StartupWMClass=Firefox
StartupNotify=true
```

This desktop file assumes that you still have firefox-esr installed, and uses its icon. **Also note that you'll need to update the desktop file to point to your home directory.**

Once you've created the desktop file run `update-desktop-database ~/.local/share/applications/` and you should be set.
