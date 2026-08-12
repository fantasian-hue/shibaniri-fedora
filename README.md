sudo dnf install niri

dconf write /org/gnome/desktop/interface/color-scheme '"prefer-dark"'

# firefox
* sudo dnf config-manager addrepo --id=mozilla --set=baseurl=https://packages.mozilla.org/rpm/firefox --set=gpgkey=https://packages.mozilla.org/rpm/firefox/signing-key.gpg --set=gpgcheck=1 --set=repo_gpgcheck=0 --set=priority=10
* sudo dnf makecache --refresh
* sudo dnf install firefox
* plasma-browser-integration - then follow steps to change about:preferences in firefox (https://www.reddit.com/r/kde/comments/1te6lk8/the_best_method_to_fix_broken_mpris_thumbnails/)
  
# nvidia
https://docs.fedoraproject.org/en-US/gaming/drivers/

# installs
sudo dnf thunar mate-polkit nautilus git playerctl pamixer pulseaudio-utils ripgrep input-remapper plasma-browser-integration lm_sensors
 
# eww
* https://elkowar.github.io/eww/
* sudo dnf install glib2-devel pkgconf-pkg-config gdk-pixbuf2-devel cairo-gobject-devel libdbusmenu-gtk3-devel gtk-layer-shell-devel
* install rust & cargo: curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
* https://docs.bswen.com/blog/2025-11-16-rustup-command-not-found/ -> to add symlinks from cargo/bin
* install eww to target folder
* sudo ln -sf ~/eww/target/release/eww /usr/local/bin/eww (eww as an example) -> symlink
