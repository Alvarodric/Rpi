# RASPBERRY PI

## AWS IOT WITH SENSORS

## STATIC IP IN RPI

```
sudo nano /etc/dhcpcd.conf
```
At the end of the file put: (being 192.168.0.4 the static ip address you want once rpi starts)
```
interface eth0
static ip_address=192.168.0.4/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```
Finally reboot
```
sudo reboot
```


## PRIVATE VPN WITH TAILSCALE


TailScale VPN setup for Linux
```
sudo apt-get install apt-transport-https &&
curl -fsSL https://pkgs.tailscale.com/stable/raspbian/buster.gpg | sudo apt-key add - &&
curl -fsSL https://pkgs.tailscale.com/stable/raspbian/buster.list | sudo tee /etc/apt/sources.list.d/tailscale.list &&
sudo apt-get update &&
sudo apt-get install tailscale &&
sudo tailscale up &&
tailscale ip -4 #get the ip 

#sudo tailscale logout
#sudo tailscale down

```

#To force all the traffic to go through the Rpi, Port forwarding is needed , the last two commands will set up the exit node:

```
echo 'net.ipv4.ip_forward = 1' | sudo tee -a /etc/sysctl.conf &&
echo 'net.ipv6.conf.all.forwarding = 1' | sudo tee -a /etc/sysctl.conf &&
sudo sysctl -p /etc/sysctl.conf &&
sudo tailscale down
sudo tailscale up --advertise-exit-node
```

Finally set up the exit mode in your admin console in the web or use this command in the RPi
```
sudo tailscale up --exit-node=<your-ip-address>
```
