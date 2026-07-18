# WAN Architecture

## 1. Purpose

This document defines the target Wide Area Network (WAN) architecture for the Enterprise Network Transformation.

The WAN provides secure, resilient, and scalable connectivity between branch offices, campus networks, data centers, cloud environments, and external services.

---

## 2. Architecture Objectives

The WAN architecture aims to:

- Provide reliable connectivity between enterprise locations.
- Support multiple WAN transport technologies.
- Improve application performance.
- Provide secure connectivity.
- Enable centralized policy and management.
- Support cloud connectivity.
- Provide high availability and path redundancy.
- Enable application-aware routing.
- Support automation and operational visibility.

---

## 3. WAN Architecture Overview

```text
                         +----------------+
                         |    Internet    |
                         +--------+-------+
                                  |
                         +--------+-------+
                         |   SD-WAN Hub   |
                         | / Data Center  |
                         +--------+-------+
                                  |
              +-------------------+-------------------+
              |                                       |
       +------+-------+                        +------+-------+
       |   Campus A   |                        |   Campus B   |
       | SD-WAN Edge  |                        | SD-WAN Edge  |
       +------+-------+                        +------+-------+
              |                                       |
          MPLS / DIA                             MPLS / DIA
              |                                       |
       +------+-------+                        +------+-------+
       |   Branch A   |                        |   Branch B   |
       | SD-WAN Edge  |                        | SD-WAN Edge  |
       +--------------+                        +--------------+
````

---

# 4. WAN Architecture Components

The WAN architecture consists of:

* Branch sites
* Campus sites
* Data centers
* Cloud environments
* WAN edge devices
* SD-WAN controllers
* Internet circuits
* MPLS circuits
* Private connectivity
* Security platforms
* Monitoring systems

---

# 5. WAN Connectivity Model

The enterprise may use multiple transport technologies.

```text
                    +----------------+
                    | Enterprise WAN |
                    +--------+-------+
                             |
              +--------------+--------------+
              |              |              |
              v              v              v
           MPLS           Internet         4G/5G
              |              |              |
              +--------------+--------------+
                             |
                         SD-WAN Edge
```

## Transport Options

| Transport          | Primary Use                     |
| ------------------ | ------------------------------- |
| MPLS               | Private enterprise connectivity |
| Internet           | Cost-effective transport        |
| DIA                | Dedicated Internet access       |
| 4G/5G              | Backup connectivity             |
| Cloud Interconnect | Cloud connectivity              |

---

# 6. SD-WAN Architecture

```text
                    +------------------+
                    | SD-WAN Manager   |
                    +--------+---------+
                             |
                    +--------+---------+
                    | SD-WAN Controller|
                    +--------+---------+
                             |
                    +--------+---------+
                    | SD-WAN Validator  |
                    +--------+---------+
                             |
          +------------------+------------------+
          |                                     |
   +------+-------+                      +------+-------+
   | SD-WAN Edge  |                      | SD-WAN Edge  |
   | Branch A     |                      | Branch B     |
   +--------------+                      +--------------+
```

---

## 6.1 SD-WAN Manager

Provides:

* Centralized management
* Configuration
* Policy management
* Monitoring
* Reporting
* Software lifecycle management

---

## 6.2 SD-WAN Controller

Provides:

* Control-plane functions
* Route distribution
* Policy distribution
* Overlay network control

---

## 6.3 SD-WAN Validator

Provides:

* Initial device connectivity
* Orchestration assistance
* NAT traversal support
* Device onboarding

---

## 6.4 SD-WAN Edge

Provides:

* WAN connectivity
* Routing
* Application-aware forwarding
* Security
* Local breakout
* Traffic steering

---

# 7. WAN Topology Models

## 7.1 Hub-and-Spoke

```text
                    +-------------+
                    |   Hub / DC  |
                    +------+------+
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
       Branch A         Branch B         Branch C
```

### Advantages

* Simple
* Centralized control
* Easy security enforcement

### Limitations

* Hub dependency
* Potential latency
* Hub scalability requirements

---

## 7.2 Full Mesh

```text
          Branch A -------- Branch B
             |\               /|
             | \             / |
             |  \           /  |
             |   \         /   |
             |    \       /    |
             +----- Branch C --+
```

### Advantages

* Direct connectivity
* Lower latency

### Limitations

* Complexity
* Scalability challenges
* Increased operational overhead

---

## 7.3 SD-WAN Dynamic Topology

```text
Branch A
   |
   +----------+
              |
              v
         SD-WAN Fabric
              ^
              |
   +----------+
   |
Branch B
```

Traffic paths are dynamically selected based on:

* Application
* Latency
* Jitter
* Packet loss
* Link availability
* Business policy

---

# 8. WAN Routing Architecture

The WAN routing architecture may use:

* BGP
* OSPF
* EIGRP
* Static routing
* SD-WAN overlay routing

Example:

```text
                    +-------------+
                    | Data Center |
                    |    BGP      |
                    +------+------+
                           |
                         BGP
                           |
                    +------+------+
                    | SD-WAN Edge |
                    +------+------+
                           |
                         OSPF
                           |
                    +------+------+
                    | Campus LAN  |
                    +-------------+
```

---

# 9. BGP Architecture

BGP may be used for:

* Data center connectivity
* Internet connectivity
* WAN route exchange
* Cloud connectivity
* Multi-provider connectivity

```text
                 +-------------+
                 | ISP / Cloud |
                 |    AS 65001 |
                 +------+------+
                        |
                       eBGP
                        |
                 +------+------+
                 | Enterprise  |
                 |    AS 65000 |
                 +-------------+
```

---

# 10. WAN High Availability

The WAN should support redundant:

* WAN circuits
* Service providers
* SD-WAN edges
* Data center connections
* Internet connections
* Power supplies

```text
                 +-------------+
                 |   Branch    |
                 +------+------+
                        |
              +---------+---------+
              |                   |
        +-----+-----+       +-----+-----+
        |   MPLS    |       | Internet  |
        |   Link    |       |   DIA     |
        +-----------+       +-----------+
```

---

# 11. WAN Failover

Example:

```text
Primary Path:
Branch ---> MPLS ---> Data Center

Backup Path:
Branch ---> Internet ---> SD-WAN Overlay ---> Data Center
```

The network should automatically select the best available path.

Failover criteria may include:

* Link failure
* High latency
* Excessive jitter
* Packet loss
* Application SLA violation

---

# 12. Application-Aware Routing

Traffic should be routed based on application requirements.

| Application       | Requirement          | Preferred Path        |
| ----------------- | -------------------- | --------------------- |
| Voice             | Low latency / jitter | MPLS or best SLA path |
| Video             | High bandwidth       | Internet / DIA        |
| Business Critical | High availability    | Best available path   |
| Guest Internet    | Local breakout       | Internet              |
| SaaS              | Direct Internet      | Local breakout        |

---

# 13. Direct Internet Access

Local Internet breakout can improve SaaS performance.

```text
                  Branch
                    |
                    v
              SD-WAN Edge
                    |
                    v
                 Firewall
                    |
                    v
                Internet
```

Security controls may include:

* Firewall
* Secure Web Gateway
* DNS security
* Cloud security
* CASB
* SASE integration

---

# 14. Cloud Connectivity

```text
                 +-------------+
                 | Enterprise  |
                 | WAN         |
                 +------+------+
                        |
                 +------+------+
                 | Cloud Edge  |
                 +------+------+
                        |
             +----------+----------+
             |                     |
        +----+----+           +----+----+
        | AWS     |           | Azure   |
        | Cloud   |           | Cloud   |
        +---------+           +---------+
```

Connectivity options may include:

* IPsec VPN
* Direct Connect
* ExpressRoute
* Cloud interconnect
* SD-WAN cloud integration

---

# 15. WAN Security Architecture

Security controls may include:

* Stateful firewall
* IPS/IDS
* URL filtering
* Secure VPN
* IPsec encryption
* Segmentation
* Zero Trust principles
* SASE integration

```text
Branch
  |
  v
SD-WAN Edge
  |
  v
Firewall / Security Stack
  |
  v
WAN / Internet / Cloud
```

---

# 16. WAN Segmentation

WAN traffic may be segmented using:

* VRFs
* VPNs
* Virtual Networks
* Security policies
* SD-WAN VPNs

Example:

```text
+----------------------+
| VPN 10 - Corporate   |
+----------------------+

+----------------------+
| VPN 20 - Guest       |
+----------------------+

+----------------------+
| VPN 30 - IoT         |
+----------------------+

+----------------------+
| VPN 40 - Management  |
+----------------------+
```

---

# 17. WAN and Campus Integration

```text
+------------------+
| Campus SDA       |
| Fabric           |
+--------+---------+
         |
         v
+--------+---------+
| Border Node      |
+--------+---------+
         |
         v
+--------+---------+
| SD-WAN Edge      |
+--------+---------+
         |
         v
+--------+---------+
| Enterprise WAN   |
+------------------+
```

The integration should define:

* Route exchange
* VRF mapping
* Security boundaries
* Traffic handoff
* Failure behavior

---

# 18. WAN Monitoring

The WAN should monitor:

* Circuit availability
* Latency
* Jitter
* Packet loss
* Bandwidth utilization
* Tunnel status
* Application performance
* Device health

Monitoring sources may include:

* SD-WAN analytics
* SNMP
* Streaming telemetry
* Syslog
* NetFlow
* IP SLA

---

# 19. WAN Automation

```text
Engineer
    |
    v
GitHub
    |
    v
CI/CD Pipeline
    |
    v
Automation Platform
    |
    v
SD-WAN Manager / API
    |
    v
WAN Infrastructure
```

Automation use cases:

* Site provisioning
* Template deployment
* VPN creation
* Routing configuration
* Policy deployment
* Compliance validation
* Configuration backup

---

# 20. WAN Failure Scenarios

| Failure             | Expected Behavior                   |
| ------------------- | ----------------------------------- |
| MPLS failure        | Internet path becomes active        |
| Internet failure    | MPLS or backup path is used         |
| SD-WAN Edge failure | Redundant edge takes over           |
| Controller failure  | Existing tunnels continue operating |
| Data center failure | Alternate data center is used       |
| Provider failure    | Alternate provider is selected      |
| High packet loss    | Traffic is moved to better path     |

---

# 21. WAN Design Principles

The WAN architecture follows these principles:

* Resilience by design
* Application-aware routing
* Secure connectivity
* Centralized policy
* Local Internet breakout where appropriate
* Automated provisioning
* Continuous monitoring
* Standards-based routing
* Scalable architecture

---

# 22. WAN Design Checklist

### Connectivity

* [ ] Primary WAN transport defined
* [ ] Backup transport defined
* [ ] Provider diversity evaluated
* [ ] Cloud connectivity defined

### Routing

* [ ] Routing protocol selected
* [ ] BGP design documented
* [ ] Route filtering defined
* [ ] Default route strategy defined
* [ ] Failover behavior documented

### Security

* [ ] Encryption requirements defined
* [ ] Firewall placement defined
* [ ] Segmentation defined
* [ ] Internet breakout security defined

### Operations

* [ ] Monitoring implemented
* [ ] SLA monitoring configured
* [ ] Automation defined
* [ ] Backup and recovery documented

---

# 23. Architecture Summary

The target WAN architecture provides secure, resilient, and application-aware connectivity between enterprise locations, data centers, cloud environments, and external services.

The architecture supports:

* Multiple WAN transports
* SD-WAN overlay connectivity
* Dynamic path selection
* BGP and enterprise routing
* Cloud integration
* Secure Internet breakout
* WAN segmentation
* High availability
* Centralized management
* Network automation

The WAN architecture integrates with the campus, data center, cloud, security, and automation architectures to provide a unified enterprise connectivity model.



