sudo dnf install niri
dconf write /org/gnome/desktop/interface/color-scheme '"prefer-dark"'

# firefox
* sudo dnf config-manager addrepo --id=mozilla --set=baseurl=https://packages.mozilla.org/rpm/firefox --set=gpgkey=https://packages.mozilla.org/rpm/firefox/signing-key.gpg --set=gpgcheck=1 --set=repo_gpgcheck=0 --set=priority=10
* sudo dnf makecache --refresh
* sudo dnf install firefox

# nvidia
https://docs.fedoraproject.org/en-US/gaming/drivers/

# installs
sudo dnf install thunar && sudo 
