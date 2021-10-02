# RASPBERRY PI


## HOME AUTOMATION
#INSTALL HOMEASSISTANT

```
sudo apt-get update
sudo apt-get install -y python3 python3-dev python3-venv python3-pip libffi-dev libssl-dev libjpeg-dev zlib1g-dev autoconf build-essential libopenjp2-7 libtiff5 libturbojpeg tzdata
sudo useradd -rm homeassistant -G dialout,gpio,i2c
sudo mkdir /srv/homeassistant
sudo chown homeassistant:homeassistant /srv/homeassistant
python3 -m pip install wheel
pip3 install homeassistant
sudo -u homeassistant -H -s
cd /srv/homeassistant
python3 -m venv /srv/homeassistant
source /srv/homeassistant/bin/activate
hass
```
https://www.youtube.com/watch?v=lElNfFRcIx8





## AWS IOT WITH SENSORS


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
sudo tailscale up --exit-node=<your-ip-address>
```
