# Campus Architecture

## 1. Purpose

This document defines the target enterprise campus network architecture, including the physical topology, logical design, network layers, redundancy, routing, segmentation, wireless connectivity, and integration with the Cisco SD-Access fabric.

The architecture is designed to provide secure, scalable, resilient, and centrally managed campus connectivity.

---

## 2. Architecture Objectives

The campus architecture aims to:

- Provide highly available wired and wireless connectivity.
- Support identity-based network access.
- Enable scalable network segmentation.
- Integrate with Cisco SD-Access.
- Support centralized network management.
- Improve operational visibility.
- Enable automation.
- Minimize single points of failure.

---

## 3. Campus Architecture Overview

```text
                         Internet / Cloud
                                |
                         +------+------+
                         |   Firewall  |
                         +------+------+
                                |
                         +------+------+
                         | WAN / SD-WAN|
                         +------+------+
                                |
                     +----------+----------+
                     |                     |
              +------+-------+      +------+-------+
              | Border Node  |      | Border Node  |
              |    1         |      |    2         |
              +------+-------+      +------+-------+
                     |                     |
                     +----------+----------+
                                |
                         SDA Fabric
                                |
              +-----------------+-----------------+
              |                                   |
       +------+-------+                    +------+-------+
       | Fabric Edge  |                    | Fabric Edge  |
       |    Node      |                    |    Node      |
       +------+-------+                    +------+-------+
              |                                   |
        +-----+-----+                       +-----+-----+
        | Access APs |                       | Wired Users|
        | / Devices  |                       | / IoT      |
        +-------------+                       +------------+
````

---

## 4. Campus Network Architecture Model

The campus architecture consists of the following major components:

### 4.1 Border Nodes

Border nodes provide connectivity between the SDA fabric and external networks.

**Responsibilities:**

* Connectivity to WAN
* Connectivity to data centers
* Connectivity to cloud environments
* Connectivity to shared services
* Route exchange with external networks
* Fabric-to-non-fabric communication

---

### 4.2 Control Plane Nodes

Control Plane nodes provide endpoint location services within the SDA fabric.

**Responsibilities:**

* Endpoint registration
* Endpoint location tracking
* Host mobility
* Fabric control-plane services

The control plane uses LISP-based control-plane functionality.

---

### 4.3 Fabric Edge Nodes

Fabric Edge nodes provide connectivity for endpoints within the SDA fabric.

**Responsibilities:**

* User connectivity
* Endpoint onboarding
* VXLAN encapsulation
* Policy enforcement
* Virtual Network assignment
* SGT handling

---

### 4.4 Intermediate Nodes

Intermediate nodes provide the IP transport infrastructure between fabric nodes.

They provide:

* IP connectivity
* Underlay transport
* Routing
* Infrastructure reachability

The intermediate network does not require awareness of endpoint-level fabric policies.

---

## 5. Physical Campus Topology

```text
                         WAN / Internet
                               |
                       +-------+-------+
                       |   Border Pair |
                       +-------+-------+
                               |
                     +---------+---------+
                     |   Core / Underlay |
                     +---------+---------+
                               |
             +-----------------+-----------------+
             |                                   |
      +------+-------+                    +------+-------+
      | Fabric Edge  |                    | Fabric Edge  |
      | Switch Pair  |                    | Switch Pair  |
      +------+-------+                    +------+-------+
             |                                   |
       Access Layer                         Access Layer
             |                                   |
       Users / IoT                         Users / IoT
```

---

## 6. Logical Architecture

The campus architecture is divided into:

```text
+----------------------------------------------+
|              Business Services               |
+----------------------------------------------+
|              Security Policies               |
|             ISE / SGT / Firewall              |
+----------------------------------------------+
|                SDA Fabric                     |
|          VXLAN / LISP / VN Segmentation       |
+----------------------------------------------+
|                IP Underlay                    |
|              Routing / Transport              |
+----------------------------------------------+
|             Physical Infrastructure           |
|        Switches / APs / Links / Devices        |
+----------------------------------------------+
```

---

## 7. Network Underlay

The underlay provides IP connectivity between the SDA fabric nodes.

### Underlay Requirements

* Stable IP connectivity
* Fast convergence
* High availability
* Scalable routing
* Loop prevention
* Infrastructure reachability

### Possible Routing Protocols

* OSPF
* IS-IS
* BGP

The selected routing protocol should be based on:

* Network size
* Operational expertise
* Convergence requirements
* Existing standards
* Scalability requirements

---

## 8. SDA Overlay

The SDA overlay provides virtualization and policy-based segmentation over the IP underlay.

```text
Endpoint
   |
   v
Fabric Edge
   |
   | VXLAN
   v
Fabric Underlay
   |
   | VXLAN
   v
Remote Fabric Edge
   |
   v
Destination Endpoint
```

The overlay supports:

* Virtual Networks
* VXLAN encapsulation
* LISP control plane
* SGT-based policy
* Endpoint mobility

---

## 9. Virtual Network Architecture

Virtual Networks provide logical isolation within the campus fabric.

```text
+----------------------+
| Virtual Network      |
|     Corporate        |
+----------------------+

+----------------------+
| Virtual Network      |
|        IoT           |
+----------------------+

+----------------------+
| Virtual Network      |
|       Guest          |
+----------------------+

+----------------------+
| Virtual Network      |
|     Operations       |
+----------------------+
```

Example Virtual Networks:

| Virtual Network | Purpose              |
| --------------- | -------------------- |
| Corporate       | Employee access      |
| Guest           | Internet-only access |
| IoT             | IoT devices          |
| Operations      | Network management   |
| Security        | Security services    |

---

## 10. Identity-Based Access

```text
Endpoint
   |
   v
802.1X / MAB
   |
   v
Cisco ISE
   |
   +--> Authentication
   |
   +--> Authorization
   |
   +--> Profiling
   |
   +--> SGT Assignment
   |
   v
Fabric Edge
   |
   v
Network Access
```

Access decisions may be based on:

* User identity
* Device identity
* Device type
* Security posture
* Location
* Authentication method

---

## 11. Segmentation Architecture

Segmentation is implemented using multiple architectural controls.

### Macro-Segmentation

Implemented using:

* Virtual Networks
* VRFs
* Firewall boundaries

### Micro-Segmentation

Implemented using:

* Security Group Tags
* Scalable Group Policies
* Identity-based access policies

```text
Corporate Users
       |
       | Policy
       v
Applications

IoT Devices
       |
       | Restricted Policy
       v
Approved Services

Guest Users
       |
       | Internet Only
       v
Internet
```

---

## 12. Wired Access Architecture

```text
User / Device
      |
      v
Access Port
      |
      v
Fabric Edge Node
      |
      v
SDA Fabric
      |
      v
Application / Service
```

The wired architecture supports:

* 802.1X
* MAB
* Dynamic authorization
* Device profiling
* SGT assignment
* Policy enforcement

---

## 13. Wireless Architecture

```text
Wireless Client
      |
      v
Wireless AP
      |
      v
Wireless Controller
      |
      v
SDA Fabric
      |
      v
Application / Internet
```

Wireless access should integrate with:

* Cisco ISE
* Identity services
* SDA fabric
* Centralized management
* Network assurance

---

## 14. High Availability

Critical campus components should be deployed redundantly.

### High Availability Components

* Border nodes
* Control Plane nodes
* Fabric Edge nodes
* Core infrastructure
* WAN connectivity
* Firewalls
* Authentication services
* Wireless infrastructure

```text
                 +----------------+
                 |   Border Node 1|
                 +--------+-------+
                          |
                    Redundant Links
                          |
                 +--------+-------+
                 |   Border Node 2|
                 +----------------+
```

---

## 15. Network Management

The campus architecture is centrally managed through Catalyst Center.

```text
Engineer
    |
    v
Catalyst Center
    |
    +--> Discovery
    |
    +--> Provisioning
    |
    +--> Configuration
    |
    +--> Assurance
    |
    +--> Automation
    |
    v
Campus Infrastructure
```

---

## 16. Monitoring and Observability

The campus network should provide visibility into:

* Device health
* Interface status
* Client health
* Application performance
* Authentication failures
* Network faults
* Capacity utilization

Data sources may include:

* Streaming telemetry
* SNMP
* Syslog
* NetFlow
* Platform assurance data

---

## 17. Campus Security Controls

Security controls include:

* 802.1X
* MAB
* Cisco ISE
* Dynamic authorization
* SGT-based policies
* VRF/VN segmentation
* Firewall policies
* DHCP snooping
* Dynamic ARP Inspection
* IP Source Guard
* Control Plane Policing

---

## 18. Failure Scenarios

| Failure                 | Expected Behavior                                        |
| ----------------------- | -------------------------------------------------------- |
| Access link failure     | Traffic uses redundant path where available              |
| Fabric Edge failure     | Endpoint connectivity is restored through redundancy     |
| Border Node failure     | External connectivity continues through redundant border |
| Control Plane failure   | Redundant control-plane services maintain operation      |
| ISE failure             | Defined authentication fallback policy applies           |
| WAN path failure        | Traffic uses alternate path                              |
| Catalyst Center failure | Existing network services continue operating             |

---

## 19. Quality Attributes

| Attribute     | Target                           |
| ------------- | -------------------------------- |
| Availability  | High                             |
| Scalability   | High                             |
| Security      | High                             |
| Performance   | Defined by business requirements |
| Manageability | High                             |
| Automation    | High                             |
| Resilience    | High                             |

---

## 20. Architecture Summary

The target campus architecture provides a secure, scalable, resilient, and centrally managed network based on a routed IP underlay and policy-driven SDA overlay.

The architecture separates:

* Physical connectivity
* IP transport
* Virtual network segmentation
* Identity
* Security policy
* Network management


