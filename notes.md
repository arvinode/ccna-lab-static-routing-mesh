# Notes & Verification Commands

## Commands used to configure

```text
enable
configure terminal
interface <interface-name>
ip address <ip> <subnet-mask>
no shutdown
exit
ip route <destination> <mask> <next-hop>
```

## Commands used to verify

| Command | What it shows |
|---|---|
| `show ip route` | The routing table — connected, local, and static routes |
| `show ip interface brief` | All interfaces, their IPs, and up/down status |
| `ping <ip>` | Tests basic connectivity to another device |

## PC configuration

Each PC needs three things to reach other networks:

```text
IP Address     : e.g. 11.0.0.2
Subnet Mask    : 255.0.0.0
Default Gateway: the router's LAN interface IP (e.g. 11.0.0.1)
```

Without the correct default gateway, a PC can only talk to devices on its
own local network.

## Simulation Mode

Switched Packet Tracer from Realtime to **Simulation Mode** and sent a
`ping` between two PCs on different LANs. This let me watch the ICMP
packet move hop-by-hop through each router, confirming the static routes
were working correctly — not just that the ping succeeded.

## What I'd explore next

- Replacing static routes with a dynamic routing protocol (OSPF or EIGRP)
  to see how much manual work it saves in a full mesh
- Route summarization to reduce the number of `ip route` entries
- Adding ACLs to control traffic between specific LANs
