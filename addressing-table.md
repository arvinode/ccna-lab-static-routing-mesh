# IP Addressing Table

Every link in the mesh (LAN or serial) was given its own unique Class A style
network (`/8`, mask `255.0.0.0`) to keep addressing simple while learning.

> Note: fill in / correct any exact IPs from your own running-config —
> this table reflects the network numbers visible in the topology diagram.

## LAN networks (Router ↔ Switch ↔ PCs)

| Network | Connected to | Router Interface |
|---|---|---|
| 11.0.0.0/8 | Router1 LAN — PC1-1, PC1-2 | Gig0/0 |
| 12.0.0.0/8 | Router2 LAN — PC2-1-1, PC2-1-2 | Gig0/1 |
| 13.0.0.0/8 | Router2 LAN — PC2-2-1, PC2-2-2 | Gig0/2 |
| 14.0.0.0/8 | Router3 LAN — PC3-1 | Gig0/1 |
| 15.0.0.0/8 | Router4 LAN — PC4-1, PC4-2 | Gig0/1 |
| 16.0.0.0/8 | Router5 LAN — PC5-1, PC5-2 | Gig0/1 |

## Serial (mesh) links — Router ↔ Router

| Network | Purpose |
|---|---|
| 10.0.0.0/8 | Serial link between two mesh routers |
| 20.0.0.0/8 | Serial link between two mesh routers |
| 30.0.0.0/8 | Serial link between two mesh routers |
| 40.0.0.0/8 | Serial link between two mesh routers |
| 50.0.0.0/8 | Serial link between two mesh routers |
| 60.0.0.0/8 | Serial link between two mesh routers |
| 70.0.0.0/8 | Serial link between two mesh routers |
| 80.0.0.0/8 | Serial link between two mesh routers |
| 90.0.0.0/8 | Serial link between two mesh routers |
| 100.0.0.0/8 | Serial link between two mesh routers |

## PC configuration example

Every PC was configured with an IP in its LAN's network, and the router's
LAN interface as the default gateway:

```text
IP Address     : 11.0.0.2
Subnet Mask    : 255.0.0.0
Default Gateway: 11.0.0.1
```
