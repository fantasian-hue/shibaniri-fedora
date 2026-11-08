sudo dnf install niri

dconf write /org/gnome/desktop/interface/color-scheme '"prefer-dark"'

# firefox
* sudo dnf config-manager addrepo --id=mozilla --set=baseurl=https://packages.mozilla.org/rpm/firefox --set=gpgkey=https://packages.mozilla.org/rpm/firefox/signing-key.gpg --set=gpgcheck=1 --set=repo_gpgcheck=0 --set=priority=10
* sudo dnf makecache --refresh
* sudo dnf install firefox
* plasma-browser-integration - then follow steps to change about:preferences in firefox (https://www.reddit.com/r/kde/comments/1te6lk8/the_best_method_to_fix_broken_mpris_thumbnails/)
* i.e. you need to create a file ~/.mozilla/native-messaging-hosts/org.kde.plasma.browser_integration.json
* with this as it's contents 
{
"name": "org.kde.plasma.browser_integration",
"description": "Native connector for KDE Plasma",
"path": "/usr/bin/plasma-browser-integration-host",
"type": "stdio",
"allowed_extensions": ["plasma-browser-integration@kde.org"]
}

# nvidia
https://docs.fedoraproject.org/en-US/gaming/drivers/

# installs
sudo dnf thunar mate-polkit nautilus git playerctl pamixer pulseaudio-utils ripgrep input-remapper plasma-browser-integration lm_sensors sysstat cava feh mpv rsync swaybg qbittorrent fastfetch ffmpegthumbnailer snes9x-gtk ly audit2search
 
# eww
* https://elkowar.github.io/eww/
* sudo dnf install glib2-devel pkgconf-pkg-config gdk-pixbuf2-devel cairo-gobject-devel libdbusmenu-gtk3-devel gtk-layer-shell-devel
* install rust & cargo: curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
* https://docs.bswen.com/blog/2025-11-16-rustup-command-not-found/ -> to add symlinks from cargo/bin
* install eww to target folder
* sudo ln -sf ~/eww/target/release/eww /usr/local/bin/eww (eww as an example) -> symlink

# matugenfox
* https://github.com/Ubaidullah-Web-Dev/MatugenFox
* install extension

# zed
* https://zed.dev/download

# chmod
* chmod -R +x ~/.config/eww/scripts && chmod -R +x ~/.config/niri/scripts && chmod +x ~/.config/zed/wal/pywal-to-zed.sh

# swayidle
set up swayidle on startup - https://niri-wm.github.io/niri/Example-systemd-Setup.html

# ly
* sudo systemctl enable ly@tty2.service
* had issues with fedora, follow steps here: https://codeberg.org/fairyglade/ly under Fedora
* sudo ausearch -m avc -ts recent
* If SELinux is denying process context transition, you will see this output:
* denied { transition } for pid=XXXX comm="ly" path="/usr/bin/bash"
scontext=system_u:system_r:unconfined_service_t:s0
tcontext=unconfined_u:unconfined_r:unconfined_t:s0
tclass=process permissive=0
* install audit2search
* sudo ausearch -m avc -ts recent | audit2allow -M ly-local
* sudo semodule -i ly-local.pp

* font was acting up, so had to change tty font
* sudo nano /etc/vconsole.conf
* changed font to "cp865-8x14", terminal fonts for fedora stored in /usr/lib/kbd/consolefonts/
* sudo nano /etc/ly/config.ini

# todo
sudo dnf install gtklock swayidle

# notes
* must turn autostart on for input-remapper
