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
@reboot sudo docker start ros6
```
### RouterOS 7
- Open crontab
```
sudo crontab -e
```
- Add this command
```
@reboot sudo docker start ros7
```
