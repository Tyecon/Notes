## Proxmox
- VM Ubuntu 23.10, Linux 6.5. Docker, Turnkey, or OpenMediaVault could work too.
- RAM: Depends on mods and amount of people. 10GB per server+2GB for OS is good enough.
- CPU: Match sockets, cores, and vcpus to the hardware, or leave some cores for other VMs. Type: host. Enable NUMA for >1 socket. Minecraft pre 1.14 doesn't multi-thread very well anyways.
- Hard Disk: 50-100GB for a world border around 10k, a couple backups, and <10 players is fine. 50 players +100k border will need TBs. Start low and balloon as needed. Prefer SSD/NVME over hard disk. VirtIO SCSI Controller, Cache: Write back (will lose cache on power loss/system crash), IO Thread[x], SSD Emulation[x], Backup[x].
- Network: VirtIO, copy the bridge MAC to IP-MAC binding in router. Firewall optional.
## Security
Create a Game-servers VLAN. ACL the Game-servers VLAN from ANY to SERVERIP TCP and UDP on 25565. ACL from Home VLAN to Gameservers VLAN TCP to 8443 and 22. Not every router can do this.  
Give the server a static IP-MAC binding then port forward from ANY to SERVERIP:25565.  
Certain mods like in game voice chat might need extra ports.
```
#Uncomplicated firewall
sudo su -
SERVERIP=192.168.25.56/24
HOMENET=192.168.1.1/24
#Change the IPs to your network's configuration
apt install -y ufw
ufw allow from $HOMENET to $SERVERIP port 22
ufw allow from $HOMENET to $SERVERIP port 8443
ufw allow 25565
ufw deny 8443
#If you screw up 22 (ssh) you will need to KVM or physically into the server. Skip if remote.
ufw deny 22
ufw enable
ufw status numbered
```
Test your ssh, web panel, and local+global Minecraft afterwards. Cloudflare can provide a .win DNS & proxy to hide your IP for cheap.
## CraftyControl
https://docs.craftycontrol.com/pages/getting-started/installation/linux/#manual-installation-steps-for-ubuntudebian-centos
