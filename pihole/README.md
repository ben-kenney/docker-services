# Instructions

Just run ```docker-compose up -d --build ```


## Setup

### Router settings
In router settings, point the DNS server to the machine that pihole is running on.
For example, 192.168.50.143

### Ubuntu host

[Turn off Ubuntu DNS services](https://www.reddit.com/r/pihole/comments/csw5z8/installing_pihole_via_docker_address_already_in/) which use port 53 (check with ```netstat -tlpn```)

```
sudo systemctl disable systemd-resolved.service
sudo systemctl stop systemd-resolved
```

In addition, follow instructions from [here](https://www.smarthomebeginner.com/run-pihole-in-docker-on-ubuntu-with-reverse-proxy/):

```sudo nano /etc/NetworkManager/NetworkManager.conf``` and add ```dns=default``` under ```[main]```

then

```
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
sudo service network-manager restart
```

### Pihole admin interface
To resolve machine names, Settings -> DNS -> (check) Use conditional forwarding with:

> Local network: 192.168.50.0/24  
IP address of router: 192.168.50.1  

## To upgrade
May need to edit your router config and point it to a default DNS server like google's 8.8.8.8. The reason is that you need to shutdown pihole, but when pihole is down, you won't be able to download the updated pihole version.
