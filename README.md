# Free-Minecraft-Server-Tutorial

- [Introduction](#introduction)
- [Creating a Ubuntu Virtual Machine Instance](#creating-a-ubuntu-virtual-machine-instance)
- [Install OpenJDK](#install-openjdk)
- [Install Crafty](#install-crafty)
- [Configure Crafty Ports](#configure-crafty-ports)
- [Connecting to your Crafty](#connecting-to-your-crafty)


## Introduction


## Creating a Ubuntu Virtual Machine Instance


## Install OpenJDK

```
 sudo apt update && sudo apt upgrade
```
```
 sudo apt install openjdk-21-jre-headless git
```

## Install Crafty

Consider following the crafty Linux install guide right here.
I recommend installing the systemd service as well as the more stable version (master).

```
 mkdir minecraft-server
```
```
 cd minecraft-server
```

```
 git clone https://gitlab.com/crafty-controller/crafty-installer-4.0.git
 cd crafty-installer-4.0
 sudo ./install_crafty.sh

```

Follow crafty installing steps

```
sudo systemctl enable crafty
```

```
 sudo systemctl start crafty
```

```
 sudo journalctl -u crafty.service -n 100
```

## Configure Crafty Ports

```
 sudo nano /etc/iptables/rules.v4
```


Make sure to add this lines:

Uncomment port 8123 for Dynmap support

```
-A INPUT -p tcp --dport 8000 -j ACCEPT
-A INPUT -p tcp --dport 8443 -j ACCEPT
#-A INPUT -p tcp --dport 8123 -j ACCEPT
-A INPUT -p tcp --match multiport --dports 25500:25600 -j ACCEPT
-A INPUT -p udp --match multiport --dports 25500:25600 -j ACCEPT
```

```
sudo iptables-restore < /etc/iptables/rules.v4
```

## Connecting to your Crafty


