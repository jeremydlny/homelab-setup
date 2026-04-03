# Pi-hole

DNS filtering and DHCP server running on the NAS via Docker with macvlan networking.

## Stack

- Pi-hole v6 (Docker)
- macvlan network — Pi-hole has its own IP on the local network
- [Quad9](https://quad9.net/) (filtered, DNSSEC) as upstream DNS
- [HaGeZi Multi PRO blocklist](https://github.com/hagezi/dns-blocklists)

## Network

- Pi-hole IP: `192.168.1.5`
- DHCP range: `192.168.1.10` to `192.168.1.150`
- Gateway: `192.168.1.1`
- NAS interface: `eth1`

## Setup
```bash
cd /Volume1/docker/pihole
docker-compose up -d
```

## Access

Dashboard available at `http://192.168.1.5/admin`

## Notes

- macvlan mode required for DHCP to work on TerramasterOS
- DHCP managed by Pi-hole (disabled on router)
- All devices on the network automatically use Pi-hole as DNS
- NAS itself cannot access Pi-hole directly due to macvlan isolation
