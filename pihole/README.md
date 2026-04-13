# Pi-hole + Unbound

DNS filtering, DHCP server and recursive DNS resolver running on the NAS via Docker with macvlan networking.

## Stack

- Pi-hole v6 (Docker)
- [Unbound](https://nlnetlabs.nl/projects/unbound/) — recursive DNS resolver (no third-party DNS)
- macvlan network — each service has its own IP on the local network
- [HaGeZi Multi PRO blocklist](https://github.com/hagezi/dns-blocklists)

## Network

- Pi-hole IP: `192.168.1.5`
- Unbound IP: `192.168.1.6`
- DHCP range: `192.168.1.10` to `192.168.1.150`
- Gateway: `192.168.1.1`
- NAS interface: `eth1`

## DNS Flow
Client → Pi-hole (192.168.1.5) → Unbound (192.168.1.6) → Root DNS servers

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
- Unbound resolves DNS recursively — no dependency on Quad9 or Cloudflare
- NAS itself cannot access Pi-hole/Unbound directly due to macvlan isolation
