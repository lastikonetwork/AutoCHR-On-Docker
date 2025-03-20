# AutoCHR-On-Docker
- This is an automated script that can run a Mikrotik CHR image inside a Docker container on a non-KVM VPS.
# Build Local Image with Automated Script
### RouterOS 6
```
bash <(wget -qO- https://raw.githubusercontent.com/lastikonetwork/AutoCHR-On-Docker/refs/heads/main/RoS6/v6.sh)
```

### RouterOS 7
```
bash <(wget -qO- https://raw.githubusercontent.com/lastikonetwork/AutoCHR-On-Docker/refs/heads/main/RoS7/v7.sh)
```

- Full Example with Port Mapping

```
sudo docker run --name mikrotik-chr-6 --restart unless-stopped -p 8291:8291 -p 3389:3389 -p 8728:8728 -p 8729:8729 -p 2222:22 -p 8080:80 -p 443:443 -p 2121:21 mikrotik-chr-6
```

```
sudo docker run --name mikrotik-chr-6 --restart unless-stopped \
    -p 7000:8291 \
    -p 7001:80 \
    -p 7002:443 \
    -p 7003:22 \
    -p 7004:23 \
    -p 7005:21 \
    -p 7006:53/udp \
    -p 7007:53/tcp \
    -p 7008:123/udp \
    -p 7009:8728 \
    -p 7010:8729 \
    -p 7011:2210 \
    -p 7012:179 \
    -p 7013:8292 \
    -p 7014:1194/udp \
    -p 7015:1194/tcp \
    -p 7016:1701/udp \
    -p 7017:1723 \
    -p 7018:500/udp \
    -p 7019:4500/udp \
    -p 7020:50/tcp \
    -p 7021:51/tcp \
    -p 7022:1812/udp \
    -p 7023:1813/udp \
    mikrotik-chr-6
```

# Expose Port
| Service          | Protocol | Port |
|------------------|----------|------|
| Winbox           | TCP      | 8291 |
| HTTP             | TCP      | 80   |
| HTTPS            | TCP      | 443  |
| SSH              | TCP      | 22   |
| Telnet           | TCP      | 23   |
| FTP              | TCP      | 21   |
| DNS              | UDP/TCP  | 53   |
| NTP              | UDP      | 123  |
| API              | TCP      | 8728 |
| API-SSL          | TCP      | 8729 |
| The Dude Server  | TCP      | 2210 |
| BGP              | TCP      | 179  |
| MPLS             | TCP      | 8292 |
| OVPN             | TCP/UDP  | 1194 |
| L2TP             | UDP      | 1701 |
| PPTP             | TCP      | 1723 |
| IPSec            | UDP/TCP  | 500, 4500, 50, 51 |
| Radius           | UDP      | 1812 |
| Radius Accounting| UDP      | 1813 |

# Issues
If the container does not start automatically when your VPS reboots, create a cron job.

### RouterOS 6
- Open crontab
```
sudo crontab -e
```
- Add this command
```
@reboot sudo docker start mikrotik-chr-6
```
### RouterOS 7
- Open crontab
```
sudo crontab -e
```
- Add this command
```
@reboot sudo docker start mikrotik-chr-6
```
