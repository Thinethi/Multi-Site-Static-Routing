**Static Routing Network Project**

A Cisco Packet Tracer project demonstrating **static routing** across a multi-router topology with multiple LANs, serial WAN links, and end devices.

---

**Project Overview**

This project explains how static routing is used to manually route traffic between multiple networks in a fixed topology.
The network consists of:

* **4 Routers** (R-01, R-02, R-03, R-04)
* Multiple **LANs** with PCs and switches
* **Serial WAN links** connecting routers
* Manually configured **static routes** for all remote networks

This ensures **end-to-end communication** across all subnets.

---

**Network Topology**

The topology includes:

* R-01 → LANs: **192.168.1.0/24, 192.168.2.0/24**
* R-02 → LANs: **192.168.4.0/24, 192.168.5.0/24**
* R-03 → LANs: **192.168.7.0/24, 192.168.8.0/24**
* R-04 → LANs: **192.168.9.0/24, 192.168.10.0/24**

Serial link networks:

* R-01 ↔ R-02 → **192.168.3.0/24**
* R-02 ↔ R-03 → **192.168.6.0/24**
* R-03 ↔ R-04 → **192.168.8.0/24**

---

**Basic Router Configuration (Sample)**

**R-01**

```bash
interface g0/0
 ip address 192.168.1.1 255.255.255.0
interface g0/1
 ip address 192.168.2.1 255.255.255.0
interface s0/1/0
 ip address 192.168.3.1 255.255.255.0
 clock rate 64000
```

**R-02**

```bash
interface g0/0
 ip address 192.168.4.1 255.255.255.0
interface g0/1
 ip address 192.168.5.1 255.255.255.0
interface s0/1/0
 ip address 192.168.3.2 255.255.255.0
interface s0/1/1
 ip address 192.168.6.1 255.255.255.0
 clock rate 64000
```

---

**Static Routing Configuration**

**R-01**

```bash
ip route 192.168.4.0 255.255.255.0 192.168.3.2
ip route 192.168.5.0 255.255.255.0 192.168.3.2
ip route 192.168.7.0 255.255.255.0 192.168.3.2
ip route 192.168.8.0 255.255.255.0 192.168.3.2
ip route 192.168.9.0 255.255.255.0 192.168.3.2
ip route 192.168.10.0 255.255.255.0 192.168.3.2
```

**R-02**

```bash
ip route 192.168.1.0 255.255.255.0 192.168.3.1
ip route 192.168.2.0 255.255.255.0 192.168.3.1
ip route 192.168.7.0 255.255.255.0 192.168.6.2
ip route 192.168.8.0 255.255.255.0 192.168.6.2
ip route 192.168.9.0 255.255.255.0 192.168.6.2
ip route 192.168.10.0 255.255.255.0 192.168.6.2
```

**R-03**

```bash
ip route 192.168.1.0 255.255.255.0 192.168.6.1
ip route 192.168.2.0 255.255.255.0 192.168.6.1
ip route 192.168.4.0 255.255.255.0 192.168.6.1
ip route 192.168.5.0 255.255.255.0 192.168.6.1
ip route 192.168.9.0 255.255.255.0 192.168.8.3
ip route 192.168.10.0 255.255.255.0 192.168.8.3
```

**R-04**

```bash
ip route 192.168.1.0 255.255.255.0 192.168.8.2
ip route 192.168.2.0 255.255.255.0 192.168.8.2
ip route 192.168.4.0 255.255.255.0 192.168.8.2
ip route 192.168.5.0 255.255.255.0 192.168.8.2
ip route 192.168.7.0 255.255.255.0 192.168.8.2
ip route 192.168.8.0 255.255.255.0 192.168.8.2
```

**Testing**

Use:

* **ping** to test connectivity
* **traceroute** to verify path
  All PCs should reach each other across all routers.


 **Conclusion**

This project successfully shows how static routing can be used in multi-router networks for predictable and controlled routing. Ideal for students learning routing fundamentals.


