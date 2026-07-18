# Campus Gap Analysis

## 1. Purpose

This document identifies the gaps between the current campus network architecture and the target campus architecture.

The analysis focuses on campus design, switching, routing, segmentation, identity-based access, Cisco SD-Access, high availability, automation, and observability.

The objective is to define the transformation required to move from a traditional campus network to a modern, secure, policy-driven, and automated campus architecture.

---

# 2. Scope

This analysis covers:

- Campus topology
- Access layer
- Distribution layer
- Core layer
- Layer 2 and Layer 3 design
- VLANs and VRFs
- Spanning Tree
- Routing
- High availability
- Identity and access control
- Cisco ISE
- Cisco SD-Access
- Security Group Tags
- Catalyst Center
- Automation
- Observability

---

# 3. Campus Transformation Overview

```text
+-------------------------+
| Current Campus Network  |
| Traditional Architecture|
+------------+------------+
             |
             v
+------------+------------+
| Gap Analysis            |
|                         |
| L2 Complexity           |
| Static Segmentation     |
| Manual Operations       |
| Limited Identity        |
| Limited Visibility      |
+------------+------------+
             |
             v
+------------+------------+
| Target Campus Network   |
| SD-Access / Policy-Based|
+-------------------------+
````

---

# 4. Current Campus Architecture

The current campus network may be based on a traditional hierarchical architecture.

```text
                         +----------------+
                         | Core Layer     |
                         +-------+--------+
                                 |
                 +---------------+---------------+
                 |                               |
                 v                               v
        +--------+--------+             +--------+--------+
        | Distribution 1  |             | Distribution 2  |
        +--------+--------+             +--------+--------+
                 |                               |
          +------+-------+                 +-----+--------+
          |              |                 |              |
          v              v                 v              v
       Access         Access            Access         Access
       Switches       Switches          Switches       Switches
```

Typical characteristics:

* VLAN-based segmentation
* STP dependency
* Manual VLAN provisioning
* Static ACLs
* Device-centric operations
* Limited identity awareness
* Limited centralized orchestration

---

# 5. Target Campus Architecture

The target architecture should provide a policy-driven and identity-aware campus network.

```text
                         +------------------+
                         | Enterprise / DC  |
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Border Node      |
                         +--------+---------+
                                  |
                         +--------+---------+
                         | SD-Access Fabric |
                         +--------+---------+
                                  |
                         +--------+---------+
                         | Fabric Edge      |
                         +--------+---------+
                                  |
                         +--------+---------+
                         | Users / Devices  |
                         +------------------+
```

Target capabilities:

* Cisco SD-Access
* Catalyst Center
* Cisco ISE
* Fabric Edge Nodes
* Control Plane Nodes
* Border Nodes
* Intermediate Nodes
* Virtual Networks
* Scalable Groups
* Identity-based policies

---

# 6. Campus Architecture Gap

| Area           | Current State         | Target State               | Gap                          | Priority |
| -------------- | --------------------- | -------------------------- | ---------------------------- | -------- |
| Architecture   | Traditional hierarchy | SD-Access fabric           | Architectural transformation | High     |
| Segmentation   | VLAN-based            | VN/VRF + SGT               | Static segmentation          | High     |
| Access Control | ACL-based             | Identity-based             | Limited identity awareness   | High     |
| Provisioning   | Manual                | Catalyst Center automation | Manual operations            | High     |
| Routing        | Traditional IGP       | Fabric underlay/overlay    | Architecture modernization   | High     |
| Visibility     | Device monitoring     | Assurance and telemetry    | Limited observability        | High     |

---

# 7. Layer 2 Gap Analysis

## Current State

The current campus may have:

* Large Layer 2 domains
* VLAN extensions
* STP dependencies
* Manual VLAN configuration
* Large failure domains

```text
VLAN 100
+-------------------------------------+
| Access 1 ---- Distribution ---- Core|
|     |                               |
| Access 2 ---------------------------|
+-------------------------------------+
```

## Target State

The target architecture should minimize unnecessary Layer 2 extension.

```text
Users
  |
  v
Fabric Edge
  |
  v
Routed Underlay
  |
  v
VXLAN Overlay
  |
  v
Policy-Based Connectivity
```

## Identified Gaps

* Excessive Layer 2 dependency
* Large broadcast domains
* STP operational complexity
* Manual VLAN extension
* Increased failure-domain size

---

# 8. Layer 3 Architecture Gap

## Current State

Layer 3 routing may be concentrated at the distribution or core layer.

```text
Access
  |
  v
Distribution
  |
  v
Core
```

## Target State

The target architecture should use a routed underlay supporting the SD-Access fabric.

```text
Fabric Edge
     |
     v
Routed Underlay
     |
     v
Control Plane
     |
     v
VXLAN Overlay
```

Target capabilities:

* IP-based underlay
* IGP
* VXLAN
* LISP control plane
* Policy-based overlay
* Centralized orchestration

---

# 9. VLAN and VRF Gap

## Current State

```text
VLAN
 |
 +--> Users
 |
 +--> Servers
 |
 +--> Voice
 |
 +--> Guest
```

Segmentation is often based on VLAN and subnet boundaries.

## Target State

```text
Virtual Network
        |
        +--> Corporate VN
        |
        +--> Guest VN
        |
        +--> IoT VN
        |
        +--> Management VN
```

Target benefits:

* Improved isolation
* Reduced routing complexity
* Consistent policy
* Better scalability

---

# 10. Security Group Tag Gap

## Current State

```text
User
  |
  v
VLAN
  |
  v
Subnet
  |
  v
ACL
```

## Target State

```text
User / Device
      |
      v
Identity
      |
      v
SGT Assignment
      |
      v
SGACL Policy
      |
      v
Policy Enforcement
```

The key gap is the transition from location-based policy to identity-based policy.

---

# 11. Cisco ISE Integration Gap

## Current State

Authentication may be based on:

* Static port configuration
* Shared credentials
* VLAN assignment
* Limited endpoint profiling

## Target State

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
   +--> Profiling
   |
   +--> Authorization
   |
   +--> SGT Assignment
```

Target capabilities:

* 802.1X
* MAB
* Endpoint profiling
* Dynamic authorization
* SGT assignment
* Guest access

---

# 12. SD-Access Fabric Role Gap

The target campus architecture introduces defined fabric roles.

| Fabric Role   | Current State             | Target State             |
| ------------- | ------------------------- | ------------------------ |
| Fabric Edge   | Traditional access switch | SD-Access fabric edge    |
| Control Plane | Traditional routing       | LISP control plane       |
| Border        | Core/WAN connectivity     | Fabric border            |
| Intermediate  | Transit network           | Underlay transport       |
| Wireless      | Separate infrastructure   | Integrated fabric access |

---

# 13. Catalyst Center Gap

## Current State

```text
Engineer
   |
   v
CLI
   |
   v
Individual Device
```

## Target State

```text
Engineer
   |
   v
Catalyst Center
   |
   +--> Design
   +--> Provision
   +--> Policy
   +--> Assurance
   |
   v
Network Fabric
```

Target capabilities:

* Network design
* Device discovery
* LAN automation
* Fabric provisioning
* Policy management
* Assurance
* Software image management

---

# 14. Campus Provisioning Gap

## Current State

```text
New Switch
    |
    v
Manual Console Access
    |
    v
Manual Configuration
    |
    v
Manual Validation
```

## Target State

```text
New Switch
    |
    v
Discovery
    |
    v
LAN Automation
    |
    v
Automated Provisioning
    |
    v
Automated Validation
```

---

# 15. High Availability Gap

Assess redundancy across the campus architecture.

| Component       | Current State  | Target State       | Gap              |
| --------------- | -------------- | ------------------ | ---------------- |
| Core            | To be assessed | Redundant          | To be identified |
| Distribution    | To be assessed | Resilient          | To be identified |
| Access Uplinks  | To be assessed | Dual uplinks       | To be identified |
| Control Plane   | To be assessed | Redundant          | To be identified |
| Border Nodes    | To be assessed | Dual border        | To be identified |
| ISE             | To be assessed | Distributed/HA     | To be identified |
| Catalyst Center | To be assessed | Resilient platform | To be identified |

---

# 16. Campus Routing Gap

## Current State

Routing may depend on:

* OSPF
* EIGRP
* Static routes
* Manual route redistribution

## Target State

The target fabric should provide:

```text
Underlay
   |
   v
IGP Reachability
   |
   v
Control Plane
   |
   v
VXLAN Overlay
   |
   v
Policy-Based Forwarding
```

Key gaps may include:

* Lack of standardized IGP
* Manual route management
* Limited overlay architecture
* Inconsistent route redistribution

---

# 17. Campus Security Gap

| Security Area      | Current State  | Target State   | Gap                |
| ------------------ | -------------- | -------------- | ------------------ |
| Authentication     | To be assessed | 802.1X         | Authentication gap |
| Non-802.1X Devices | To be assessed | MAB            | Device support gap |
| Authorization      | Static         | Dynamic        | Policy gap         |
| Segmentation       | VLAN           | VN/SGT         | Segmentation gap   |
| Enforcement        | ACL            | SGACL/Policy   | Enforcement gap    |
| Visibility         | Basic          | Identity-aware | Visibility gap     |

---

# 18. Campus Automation Gap

## Current State

```text
Change Request
      |
      v
Engineer
      |
      v
CLI Configuration
      |
      v
Manual Validation
```

## Target State

```text
Design
  |
  v
Catalyst Center / Git
  |
  v
Automation
  |
  v
Policy Deployment
  |
  v
Assurance Validation
```

Automation opportunities:

* Device onboarding
* LAN automation
* VLAN/VN provisioning
* Policy deployment
* Configuration compliance
* Software upgrades

---

# 19. Campus Observability Gap

## Current State

```text
Device
  |
  v
SNMP
  |
  v
Basic Monitoring
```

## Target State

```text
Fabric
  |
  +--> Telemetry
  +--> Assurance
  +--> Client Health
  +--> Device Health
  +--> Application Experience
  |
  v
Centralized Analytics
```

Target visibility includes:

* Device health
* Fabric health
* Client health
* Application experience
* Authentication failures
* Path visibility
* Policy violations

---

# 20. Campus Operations Gap

| Capability      | Current State   | Target State                        |
| --------------- | --------------- | ----------------------------------- |
| Provisioning    | Manual          | Automated                           |
| Policy          | Device-specific | Centralized                         |
| Troubleshooting | CLI-based       | Assurance-based                     |
| Monitoring      | Device-focused  | User/service-focused                |
| Changes         | Manual          | Controlled automation               |
| Documentation   | Distributed     | Centralized architecture repository |

---

# 21. Campus Technology Gap Register

| ID       | Gap                             | Impact                      | Priority | Recommendation            |
| -------- | ------------------------------- | --------------------------- | -------- | ------------------------- |
| CAMP-001 | Traditional campus architecture | High operational complexity | High     | Implement SD-Access       |
| CAMP-002 | VLAN-based segmentation         | Limited security            | High     | Implement VN and SGT      |
| CAMP-003 | Limited 802.1X adoption         | Weak identity control       | High     | Implement ISE             |
| CAMP-004 | Manual provisioning             | Slow deployment             | High     | Implement Catalyst Center |
| CAMP-005 | STP dependency                  | Large failure domains       | High     | Increase Layer 3 design   |
| CAMP-006 | Limited assurance               | Slow troubleshooting        | High     | Implement observability   |
| CAMP-007 | Manual policy management        | Configuration inconsistency | Medium   | Centralize policy         |

---

# 22. Campus Transformation Roadmap

```text
Phase 1
Foundation
    |
    +--> IP Addressing
    +--> Hardware Readiness
    +--> Software Compatibility
    |
    v
Phase 2
Identity
    |
    +--> ISE
    +--> 802.1X
    +--> MAB
    |
    v
Phase 3
Fabric
    |
    +--> Underlay
    +--> Control Plane
    +--> Fabric Edge
    +--> Border
    |
    v
Phase 4
Policy
    |
    +--> VN
    +--> SGT
    +--> SGACL
    |
    v
Phase 5
Automation
    |
    +--> Catalyst Center
    +--> LAN Automation
    |
    v
Phase 6
Optimization
    |
    +--> Assurance
    +--> Analytics
    +--> Automation
```

---

# 23. Campus Migration Dependencies

The campus transformation may depend on:

* Hardware compatibility
* Software versions
* IP addressing
* ISE deployment
* Identity source integration
* Authentication readiness
* Network documentation
* Application dependencies
* Wireless integration
* Operations team skills

---

# 24. Campus Transformation Risks

| Risk                     | Impact | Mitigation             |
| ------------------------ | ------ | ---------------------- |
| Unsupported hardware     | High   | Hardware assessment    |
| Authentication failure   | High   | Pilot 802.1X           |
| Application dependency   | High   | Application discovery  |
| Migration downtime       | High   | Phased migration       |
| Skills gap               | Medium | Training               |
| Policy errors            | High   | Test in lab            |
| Incomplete documentation | Medium | Documentation baseline |

---

# 25. Success Metrics

The campus transformation should be measured using:

* 802.1X adoption rate
* Percentage of identity-based access
* Number of automated deployments
* Network availability
* Mean Time to Repair
* Configuration compliance
* Fabric health
* Client health
* Policy compliance

Example targets:

```text
802.1X Adoption          > 90%
Configuration Compliance > 95%
Network Availability     > 99.9%
Automated Provisioning   > 70%
```

---

# 26. Campus Gap Analysis Summary

```text
+--------------------------+
| Traditional Campus      |
| VLAN / STP / Manual     |
+------------+-------------+
             |
             v
+------------+-------------+
| Transformation Gaps     |
|                          |
| Architecture             |
| Identity                 |
| Segmentation             |
| Automation               |
| Observability            |
+------------+-------------+
             |
             v
+------------+-------------+
| Target SD-Access Campus  |
| Secure / Policy-Driven   |
| Automated / Observable   |
+--------------------------+
```

The major campus transformation priorities are:

1. Modernize the campus architecture.
2. Reduce Layer 2 dependency.
3. Implement identity-based access control.
4. Integrate Cisco ISE.
5. Introduce dynamic segmentation.
6. Implement Cisco SD-Access where appropriate.
7. Automate provisioning and policy deployment.
8. Improve campus observability and assurance.

---

## Conclusion

The campus gap analysis identifies the transformation required to move from a traditional campus network to a modern, identity-aware, policy-driven, automated, and observable architecture.

The most significant transformation is the shift:

```text
Traditional Campus
        |
        v
VLAN-Based Security
        |
        v
Manual Operations
        |
        v
Limited Visibility
```

to:

```text
SD-Access Campus
        |
        v
Identity-Based Policy
        |
        v
Automated Operations
        |
        v
End-to-End Assurance
```

This document should be used as the foundation for the campus transformation roadmap and detailed implementation planning.

