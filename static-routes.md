# Static Routes — Logic & Syntax

## Syntax

```text
ip route <destination network> <subnet mask> <next-hop IP>
```

**Meaning:** "To reach this destination network, forward the packet to this
next-hop IP address (a directly connected neighbor router)."

## Example

```text
ip route 12.0.0.0 255.0.0.0 10.0.0.2
```

This tells the router: *network 12.0.0.0 is not directly connected to me —
send anything going there to my neighbor at 10.0.0.2, and let that router
figure out the rest.*

## Rules I learned

1. **No route needed for directly connected networks.**
   The router already knows about networks on its own interfaces
   (these show as `C` and `L` in the routing table).

2. **Add a route only for remote networks** — ones reachable through another
   router.

3. **The next hop must be the neighbor router's IP address**, not the IP of
   the destination network itself. The next hop is always one hop away
   (directly connected to the router you're configuring).

4. In a full mesh, every router needs a static route for every network it
   isn't directly connected to. This is a lot of manual entries — one of
   the reasons dynamic routing protocols (like OSPF/EIGRP) exist, which is
   the natural next step after mastering static routing.

## Routing table symbols

| Symbol | Meaning |
|---|---|
| `C` | Connected network (directly attached to an interface) |
| `L` | Local — the router's own interface IP |
| `S` | Static route (manually configured) |

## Router1 — full static route list (example)

```text
ip route 12.0.0.0  255.0.0.0  10.0.0.2
ip route 13.0.0.0  255.0.0.0  10.0.0.2
ip route 14.0.0.0  255.0.0.0  60.0.0.2
ip route 15.0.0.0  255.0.0.0  70.0.0.1
ip route 16.0.0.0  255.0.0.0  50.0.0.1
ip route 20.0.0.0  255.0.0.0  10.0.0.2
ip route 30.0.0.0  255.0.0.0  60.0.0.2
ip route 40.0.0.0  255.0.0.0  70.0.0.1
ip route 80.0.0.0  255.0.0.0  10.0.0.2
ip route 90.0.0.0  255.0.0.0  50.0.0.1
ip route 100.0.0.0 255.0.0.0  10.0.0.2
```

(Repeat the same logic for Router2–Router6, using each router's own
neighbor IPs as next hops.)
