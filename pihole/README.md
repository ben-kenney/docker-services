# Instructions

Just run ```docker-compose up -d --build ```


## Setup

In router settings, point the DNS server to the machine that pihole is running on.
For example, 192.168.50.143


## To upgrade
May need to edit your router config and point it to a default DNS server like google's 8.8.8.8. The reason is that you need to shutdown pihole, but when pihole is down, you won't be able to download the updated pihole version.
