# Unbound

Recursive DNS resolver running on the NAS via Docker, used as upstream for Pi-hole.

## Stack

- Unbound (Docker)
- macvlan network — dedicated IP on the local network
- Resolves DNS queries directly from root servers (no third-party DNS)

## Network

- Unbound IP: `192.168.1.6`
- Pi-hole points to: `192.168.1.6`

## Setup

```bash
cd /Volume1/docker/unbound
docker-compose up -d
```

## Notes

- macvlan required — same network as Pi-hole
- Unbound listens on `0.0.0.0` via custom `unbound.conf`
- NAS cannot reach Unbound directly due to macvlan isolation (expected)
- Test from a device on the network: `nslookup google.com 192.168.1.6`
