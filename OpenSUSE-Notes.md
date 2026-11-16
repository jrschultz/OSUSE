# 🦎 OpenSUSE Config Notes 🗒️

Various configuration notes for OpenSUSE Linux 

## 🔄 UPDATING

### Updating Tumbleweed (Rolling)

```bash
sudo zypper refresh && sudo zypper dup --allow-vendor-change -y
```

### Updating Leap Packages 

```bash
sudo zypper refresh && sudo zypper up
```

### Updating Leap System 

```bash
sudo zypper patch
```

## 👨‍💻 REPO PACKAGES & FLATPAKS
 
🔸**List out user-installed packages and export to a file:**

```bash
zypper se -si | awk -F'|' '$1 ~ /^i\+/ && $3 ~ /package/ {gsub(/^[ \t]+|[ \t]+$/, "", $2); print $2}' | sort -u > pkglist.txt
```

🔸**Install them on a fresh install:**

```bash
sudo zypper install -y $(cat pkglist.txt)
```

🔸**List out flatpaks and export to a file:**

```bash
flatpak list --app --columns=application > flatpak-list.txt
```

🔸**Install them on a fresh install:**

```bash
xargs -a flatpak-list.txt flatpak install -y flathub
```

## 🎧 MEDIA CODECS

OpenSUSE installs only free, open, and non-patent-encumbered multimedia formats (such as Ogg, Vorbis, and FLAC) out of the box due to legal and patent constraints. To play restricted or patent-encumbered formats like MP3, MP4, H.264, H.265, DVD, and AAC, you must install external multimedia codecs—most commonly from the Packman repository.

```bash
sudo zypper in opi
```

```bash 
opi codecs
```

Follow the on-screen prompts to select your repository mirror, accept GPG keys, and let it switch packages to Packman. Restart your media player or browser when finished.

## 🛜 AVAHI 

📥 **Install dependencies:**

```bash
sudo zypper install avahi avahi-utils libavahi-client3
```

😈 **Start the Daemon:**

```bash
sudo systemctl enable --now avahi-daemon
```

🔥 **Configure Firewalld:**

```bash
sudo firewall-cmd --add-service=mdns --permanent
sudo firewall-cmd --reload
```

😈 **Restart the Daemon:**

```bash
systemctl restart avahi-daemon
```

## 📁 LOCALSEND

⤴️ **Peristent port access for LocalSend**

```bash
sudo firewall-cmd --permanent --add-port=53317/tcp
sudo firewall-cmd --permanent --add-port=53317/udp
```

✅ **Check it worked**

```bash
sudo firewall-cmd --list-ports
```

🔥 **Reload the firewall**

```bash
sudo firewall-cmd --reload
```

## 🔍 ICONS

📥 **Install Papirus icons & folders script**

```bash
sudo zypper in papirus-icon-theme papirus-folders
```

🟢 **Change colours**

```bash
papirus-folders -C green --theme Papirus-Dark
```

📋 **List colours**

```bash
papirus-folders --list
```

## 🔠 MS FONTS

**This is the equivalent of** ```ttf-mscorefonts-installer```

```bash
sudo zypper in fetchmsttfonts
```




