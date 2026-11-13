# 🗒️ OpenSUSE Config Notes

Various configuration notes for OpenSUSE Linux 🦎 

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

## 🛜 AVAHI 

📥 Install dependencies:

```bash
sudo zypper install avahi avahi-utils libavahi-client3
```

😈 Start the Daemon:

```bash
sudo systemctl enable --now avahi-daemon
```

🔥 Configure Firewalld

```bash
sudo firewall-cmd --add-service=mdns --permanent
sudo firewall-cmd --reload
```

😈 Restart the Daemon

```bash
systemctl restart avahi-daemon
```

## 📁 LOCALSEND

⤴️ Peristent port access for LocalSend

```bash
sudo firewall-cmd --permanent --add-port=53317/tcp
sudo firewall-cmd --permanent --add-port=53317/udp
```

✅ Check it worked

```bash
sudo firewall-cmd --list-ports
```

🔥 Reload the firewall

```bash
sudo firewall-cmd --reload
```

## 🔍 ICONS

📥 Install Papirus icons & folders script

```bash
sudo zypper in papirus-icon-theme papirus-folders
```

🟢 Change colours

```bash
papirus-folders -C green --theme Papirus-Dark
```

📋 List colours

```bash
papirus-folders --list
```

