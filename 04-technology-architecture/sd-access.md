# Cisco SD-Access Architecture

## 1. Purpose

This document defines the target Cisco SD-Access architecture for the Enterprise Network Transformation.

Cisco SD-Access provides a policy-driven campus architecture based on an IP underlay, VXLAN overlay, identity-based access control, virtual network segmentation, and centralized orchestration through Cisco Catalyst Center.

---

## 2. Architecture Objectives

The SD-Access architecture aims to:

- Simplify campus network operations.
- Provide identity-based network access.
- Enable macro- and micro-segmentation.
- Separate the network underlay from the policy overlay.
- Provide scalable endpoint mobility.
- Automate fabric provisioning.
- Centralize network management.
- Improve network visibility and assurance.

---

## 3. SD-Access Architecture Overview

```text
                         +------------------+
                         | Catalyst Center  |
                         | Orchestration    |
                         +--------+---------+
                                  |
                    +-------------+-------------+
                    |                           |
                    v                           v
             +-------------+             +-------------+
             | Cisco ISE   |             | IPAM / DNS  |
             | Identity    |             | DHCP        |
             +------+------+             +-------------+
                    |
                    | Policy / Identity
                    v
        +-----------+-------------------------+
        |              SDA FABRIC             |
        |                                     |
        |  +-------------+   +-------------+  |
        |  | Control     |   | Border      |  |
        |  | Plane Node  |   | Node        |  |
        |  +------+------+   +------+------+  |
        |         |                 |         |
        |         +--------+--------+         |
        |                  |                  |
        |          +-------+-------+          |
        |          | Fabric Edge   |          |
        |          | Nodes         |          |
        |          +-------+-------+          |
        |                  |                  |
        |              Endpoints              |
        +-------------------------------------+
````

---

# 4. SD-Access Architecture Components

The main components are:

1. Management Plane
2. Control Plane
3. Data Plane
4. Policy Plane
5. Underlay Network
6. Overlay Network

---

# 5. Management Plane

The management plane is provided by Cisco Catalyst Center.

```text
Engineer
    |
    v
Catalyst Center
    |
    +--> Discovery
    |
    +--> LAN Automation
    |
    +--> Fabric Creation
    |
    +--> Device Provisioning
    |
    +--> Policy Configuration
    |
    +--> Assurance
```

### Key Functions

* Device discovery
* LAN automation
* Fabric creation
* Device role assignment
* IP address management integration
* Network provisioning
* Policy configuration
* Network assurance
* Software image management

---

# 6. Control Plane

The control plane provides endpoint location services.

SD-Access uses LISP-based control-plane functionality to maintain endpoint location information.

```text
Endpoint
    |
    v
Fabric Edge Node
    |
    | Endpoint Registration
    v
Control Plane Node
    |
    | Endpoint Location Database
    v
Remote Fabric Edge
```

### Control Plane Functions

* Endpoint registration
* Endpoint location tracking
* Host mobility
* Mapping resolution
* Endpoint reachability information

---

# 7. Data Plane

The data plane transports user traffic across the fabric.

SD-Access uses VXLAN for data-plane encapsulation.

```text
Endpoint A
    |
    v
Fabric Edge A
    |
    | VXLAN Encapsulation
    v
IP Underlay
    |
    | VXLAN Tunnel
    v
Fabric Edge B
    |
    v
Endpoint B
```

### VXLAN Provides

* Overlay encapsulation
* Virtual Network separation
* Endpoint mobility
* Scalable segmentation

---

# 8. Policy Plane

The policy plane determines who can communicate with whom.

Cisco ISE provides identity and policy information.

```text
User / Device
      |
      v
Cisco ISE
      |
      +--> Identity
      |
      +--> Device Profile
      |
      +--> Authorization
      |
      +--> SGT Assignment
      |
      v
SDA Fabric
      |
      v
Policy Enforcement
```

---

# 9. SD-Access Underlay

The underlay is the IP transport network that provides connectivity between fabric nodes.

```text
+-------------+       +-------------+
| Fabric Edge |-------| Intermediate|
| Node        |       | Node        |
+-------------+       +------+------+
                              |
                       +------+------+
                       | Intermediate|
                       | Node        |
                       +------+------+
                              |
                       +------+------+
                       | Border Node |
                       +-------------+
```

## Underlay Requirements

The underlay must provide:

* IP reachability
* Fast convergence
* Stable routing
* High availability
* Loop-free connectivity
* MTU support for VXLAN
* Infrastructure reachability

---

# 10. Underlay Routing

Possible routing protocols include:

* OSPF
* IS-IS
* BGP

The routing protocol should be selected based on:

* Enterprise standards
* Network scale
* Operational expertise
* Convergence requirements
* Scalability

### Example

```text
Fabric Edge
     |
     | OSPF / IS-IS / BGP
     v
Intermediate Node
     |
     v
Control Plane / Border
```

---

# 11. SD-Access Overlay

The overlay is built on top of the IP underlay.

```text
+-----------------------------------------+
|              SDA OVERLAY                |
|                                         |
|     VXLAN + LISP + VN + SGT             |
+-----------------------------------------+
|              IP UNDERLAY                |
|          Routing / Transport            |
+-----------------------------------------+
|           Physical Infrastructure       |
|      Switches / Links / Devices         |
+-----------------------------------------+
```

The overlay provides:

* Endpoint virtualization
* Virtual Networks
* Segmentation
* Endpoint mobility
* Policy-based communication

---

# 12. Fabric Roles

## 12.1 Fabric Edge Node

The Fabric Edge Node connects endpoints to the SDA fabric.

### Responsibilities

* Endpoint attachment
* Endpoint authentication
* VXLAN encapsulation
* Policy enforcement
* SGT handling
* Virtual Network assignment

```text
Endpoint
   |
   v
Fabric Edge
   |
   | VXLAN
   v
SDA Fabric
```

---

## 12.2 Control Plane Node

The Control Plane Node maintains endpoint location information.

### Responsibilities

* Endpoint registration
* Endpoint location database
* Host mobility
* Mapping resolution

---

## 12.3 Border Node

The Border Node connects the SDA fabric to external networks.

```text
SDA Fabric
     |
     v
Border Node
     |
     +--> WAN
     |
     +--> Data Center
     |
     +--> Internet
     |
     +--> Cloud
```

---

## 12.4 Intermediate Node

Intermediate Nodes provide IP transport between fabric nodes.

They do not need to understand endpoint-level policies.

```text
Fabric Edge
     |
     v
Intermediate Network
     |
     v
Fabric Edge / Border
```

---

## 12.5 Wireless Fabric

Wireless access points connect users to the SDA fabric.

```text
Wireless Client
       |
       v
Access Point
       |
       v
Fabric Edge
       |
       v
SDA Fabric
```

---

# 13. Fabric Node Architecture

```text
                    +----------------+
                    | Control Plane  |
                    | Node           |
                    +--------+-------+
                             |
                             |
+-------------+      +-------+-------+      +-------------+
| Fabric Edge |------| IP Underlay   |------| Fabric Edge |
| Node 1      |      |               |      | Node 2      |
+------+------+      +-------+-------+      +------+------+
       |                     |                     |
       |                     |                     |
    Users                 Border                 Users
                             |
                             v
                         External WAN
```

---

# 14. Virtual Network Architecture

Virtual Networks provide macro-segmentation.

```text
+----------------------+
| VN-Corporate         |
| Employee Services    |
+----------------------+

+----------------------+
| VN-IoT               |
| IoT Devices          |
+----------------------+

+----------------------+
| VN-Guest             |
| Guest Internet       |
+----------------------+

+----------------------+
| VN-Operations        |
| Network Management   |
+----------------------+
```

### Example

| Virtual Network | Purpose            |
| --------------- | ------------------ |
| Corporate       | Employee access    |
| IoT             | IoT devices        |
| Guest           | Guest access       |
| Operations      | Network management |
| Security        | Security services  |

---

# 15. Macro-Segmentation

Macro-segmentation separates traffic into Virtual Networks.

```text
Corporate VN
      X
      |
      X
IoT VN
      X
      |
      X
Guest VN
```

Communication between Virtual Networks should be controlled through:

* Border nodes
* Firewalls
* Policy enforcement points

---

# 16. Micro-Segmentation

Micro-segmentation provides granular policy within a Virtual Network.

Security Group Tags are used to identify the source and destination security groups.

```text
Employee SGT
      |
      | Permit
      v
Application SGT

Guest SGT
      |
      | Deny
      v
Internal Server SGT
```

---

# 17. SGT Policy Matrix

```text
+-------------+-------------+----------+
| Source SGT  | Dest. SGT   | Action   |
+-------------+-------------+----------+
| Employee    | Application | Permit   |
| Employee    | Database    | Permit   |
| Guest       | Server      | Deny     |
| IoT         | Internet    | Restrict |
| Admin       | Network     | Permit   |
+-------------+-------------+----------+
```

---

# 18. Endpoint Onboarding

```text
Endpoint
    |
    v
Access Port / Wireless
    |
    v
802.1X / MAB
    |
    v
Cisco ISE
    |
    +--> Authentication
    |
    +--> Profiling
    |
    +--> Authorization
    |
    +--> SGT Assignment
    |
    v
Fabric Edge
    |
    v
Virtual Network Access
```

---

# 19. SD-Access Traffic Flow

## Same Fabric Site

```text
Endpoint A
    |
    v
Fabric Edge A
    |
    | VXLAN
    v
Fabric Edge B
    |
    v
Endpoint B
```

---

## External Network Access

```text
Endpoint
    |
    v
Fabric Edge
    |
    v
Border Node
    |
    +--> WAN
    |
    +--> Data Center
    |
    +--> Internet
    |
    +--> Cloud
```

---

# 20. SD-Access and Cisco ISE Integration

```text
+------------------+
| Cisco ISE        |
| Identity & Policy|
+--------+---------+
         |
         | Policy / Identity
         v
+--------+---------+
| Catalyst Center  |
+--------+---------+
         |
         | Orchestration
         v
+--------+---------+
| SDA Fabric       |
+------------------+
```

ISE provides:

* Authentication
* Authorization
* Endpoint profiling
* SGT assignment
* Identity information

Catalyst Center provides:

* Fabric orchestration
* Device provisioning
* Policy deployment
* Assurance

---

# 21. SD-Access Automation

```text
Engineer
    |
    v
Catalyst Center
    |
    +--> Discover Devices
    |
    +--> Build Underlay
    |
    +--> Create Fabric
    |
    +--> Assign Roles
    |
    +--> Configure VN
    |
    +--> Deploy Policy
    |
    v
SDA Infrastructure
```

Automation may include:

* LAN Automation
* Device provisioning
* Fabric creation
* Policy deployment
* Configuration validation

---

# 22. High Availability

The SDA architecture should provide redundancy for:

* Fabric Edge Nodes
* Control Plane Nodes
* Border Nodes
* Network links
* ISE PSNs
* Catalyst Center
* WAN connectivity

```text
                 +----------------+
                 | Border Node 1  |
                 +--------+-------+
                          |
                     Redundant
                      Underlay
                          |
                 +--------+-------+
                 | Border Node 2  |
                 +----------------+
```

---

# 23. MTU Requirements

VXLAN adds additional encapsulation overhead to the original packet.

Therefore, the underlay must support an appropriate MTU.

The architecture must verify:

* End-to-end MTU
* Interface MTU
* Path MTU
* VXLAN overhead
* Fragmentation behavior

MTU validation is required before production deployment.

---

# 24. SD-Access Security

Security controls include:

* 802.1X
* MAB
* Cisco ISE
* Virtual Networks
* Security Group Tags
* Firewall policies
* DHCP Snooping
* Dynamic ARP Inspection
* IP Source Guard
* Control Plane Policing

---

# 25. Failure Scenarios

| Failure                 | Expected Behavior                              |
| ----------------------- | ---------------------------------------------- |
| Fabric Edge failure     | Endpoint uses redundant path or alternate node |
| Control Plane failure   | Redundant control-plane node maintains service |
| Border Node failure     | External connectivity uses alternate border    |
| Underlay link failure   | Routing reconverges through alternate path     |
| ISE PSN failure         | Authentication uses another PSN                |
| Catalyst Center failure | Existing fabric continues operating            |
| WAN failure             | Alternate WAN path is used                     |

---

# 26. Monitoring and Assurance

The SD-Access architecture should monitor:

* Fabric node health
* Endpoint health
* Authentication status
* Fabric control-plane status
* VXLAN tunnels
* Underlay routing
* Application performance
* Policy violations

Monitoring sources include:

* Catalyst Center Assurance
* Cisco ISE
* Streaming telemetry
* SNMP
* Syslog
* NetFlow

---

# 27. SD-Access Design Checklist

### Underlay

* [ ] IP addressing plan defined
* [ ] Routing protocol selected
* [ ] MTU validated
* [ ] Redundant paths available
* [ ] Loopback addressing defined

### Fabric

* [ ] Fabric site created
* [ ] Fabric Edge Nodes identified
* [ ] Control Plane Nodes identified
* [ ] Border Nodes identified
* [ ] Intermediate Nodes identified

### Identity

* [ ] ISE integrated
* [ ] 802.1X configured
* [ ] MAB requirements documented
* [ ] Endpoint profiling configured
* [ ] Authorization policies defined

### Segmentation

* [ ] Virtual Networks defined
* [ ] SGTs defined
* [ ] Policy matrix created
* [ ] External connectivity defined

### Operations

* [ ] Monitoring implemented
* [ ] Assurance enabled
* [ ] Backup configured
* [ ] Failure scenarios tested
* [ ] Operational procedures documented

---

# 28. Architecture Summary

Cisco SD-Access provides a policy-driven enterprise campus architecture that separates the network transport from identity and security policy.

The architecture consists of:

* IP underlay
* VXLAN overlay
* LISP-based control plane
* Fabric Edge Nodes
* Control Plane Nodes
* Border Nodes
* Intermediate Nodes
* Virtual Networks
* Security Group Tags
* Cisco ISE
* Catalyst Center

Together, these components provide a scalable, secure, automated, and identity-based enterprise network architecture.

The SD-Access architecture enables the enterprise to move from traditional VLAN-based designs toward a modern policy-driven network model.



