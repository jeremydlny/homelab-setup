# Pi-hole

DNS filtering server running on the NAS via Docker.

## Stack

- Pi-hole v6 (Docker)
- Quad9 (filtered, ECS, DNSSEC) as upstream DNS
- HaGeZi Multi PRO blocklist

## Setup
```bash
cd /Volume1/docker/pihole
docker-compose up -d
```

## Access

Dashboard available at `http://NAS_IP:8080/admin`

## Notes

- DHCP managed by the router (Livebox 5)
- DNS configured manually on each device
- IPv6 disabled on upstream DNS to avoid connectivity issues
