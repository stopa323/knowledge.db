## Loops on L2
- Broadcast storms
- Unstable MAC address tables

## Glossary
**Root Bridge** 

### Root Port
The link connected to the root bridge, or the shortest path to the root bridge.  If more than one link connects to the root bridge, then a port cost is determined by checking the bandwidth of each link. The lowest cost port becomes the root port. If multiple links have the same cost, the bridge with the lower advertising Bridge ID is used. Since multiple links can be from the same device, the lowest port number will be used.

TLDR: direct > bandwidth (lowest) > bridge ID (lowest) > port number (lowest)

### Designated Port
Port through which connected segment has best path to the *Root Bridge*

### Non-designated Port
Port which is not Root nor designated port; put into blocking state

## STP Election process

1. Elect a **Root Bridge**
2. Place all root interfaces in forwarding state
3. Each non-root bridge selects its **Root Port**
4. Remaining links choose **Designated Port**
5. All other ports are put to blocking state

### Selecting Root Bridge

Switches exchange BPDUs containing:
 * Root cost - cost to root bridge 
 * Bridge ID - [STP priority(32769 + VLAN number)][MAC address]
 
Each switch listens for BPDU as the roots, as the information converges switch with lowest BID is selected Root Bridge

### Select Root Ports
Port with lowest root cost is chosen. If multiple ports with lowest cost exist: 
lowest neighbour BID > lowest neighbour port priority > lowest neighbour port number

### Designated ports
Similarly to Root ports

## Timers

### Hello timer
Interval at which bridge will create and send Hello messages (2s default).

### MaxAge
Time after which switch will realize sth is wrong (10x Hello timer default)

### Forward delay
Time bewteen Listening and Learing states [Learining and Forwarding as well] (15s default)

# References
[na jutube](https://www.youtube.com/watch?v=japdEY1UKe4)
