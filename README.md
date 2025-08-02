# LAN Scenario 05 – DHCP Configuration Using a Cisco Router

## 🎯 Objective
To configure a Cisco router as a DHCP server that automatically assigns IP addresses to LAN devices.

## 🧱 Devices Used
- 1× Router
- 1× Switch
- 3× PCs
- Copper Straight-through cables

## 🧠 Network Topology

The router provides IP addresses to the PCs through DHCP.


## 🌐 IP Configuration

| Device   | Interface   | IP Address      | Notes                  |
|----------|-------------|------------------|-------------------------|
| Router   | Gig0/0      | 192.168.10.1     | DHCP Server             |
| PC0      | —           | DHCP             | Gets IP from router     |
| PC1      | —           | DHCP             | Gets IP from router     |
| PC2      | —           | DHCP             | Gets IP from router     |

### DHCP Pool:
- **Network:** 192.168.10.0/24
- **Default Gateway:** 192.168.10.1
- **DNS Server:** 8.8.8.8
- **Excluded IPs:** 192.168.10.1 – 192.168.10.9

## 🔧 Router Configuration

```bash
interface gig0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
 ip nat inside
exit

ip dhcp excluded-address 192.168.10.1 192.168.10.9

ip dhcp pool LAN_POOL
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 8.8.8.8
