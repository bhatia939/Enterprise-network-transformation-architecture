# WAN Gap Analysis

## 1. Purpose

This document identifies the gaps between the current enterprise WAN architecture and the target WAN architecture.

The objective is to define the transformation required to move from a traditional, manually operated WAN to a secure, resilient, application-aware, automated, and cloud-ready WAN architecture.

---

## 2. Scope

This analysis covers:

- Enterprise WAN architecture
- MPLS connectivity
- Internet connectivity
- SD-WAN
- Branch connectivity
- Data center connectivity
- Cloud connectivity
- Routing
- VPN and encryption
- High availability
- Application-aware routing
- WAN security
- Automation
- Monitoring and observability

---

# 3. WAN Transformation Overview

```text
+--------------------------+
| Current WAN              |
| MPLS / Internet / VPN    |
| Manual Operations        |
+------------+-------------+
             |
             v
+------------+-------------+
| Identified Gaps          |
|                          |
| High Cost                |
| Limited Agility          |
| Manual Provisioning      |
| Limited Visibility       |
| Limited Cloud Integration|
+------------+-------------+
             |
             v
+------------+-------------+
| Target WAN               |
| Secure SD-WAN            |
| Automated / Cloud-Ready  |
+--------------------------+
````

---

# 4. Current WAN Architecture

A traditional enterprise WAN may use MPLS as the primary transport with Internet VPN as a backup.

```text
                         +----------------+
                         | Data Center    |
                         +--------+-------+
                                  |
                                  |
                         +--------+-------+
                         | MPLS Network   |
                         +--------+-------+
                           /       |       \
                          /        |        \
                         v         v         v
                    Branch 1   Branch 2   Branch 3
```

Additional connectivity may include:

* Internet VPN
* Private WAN
* MPLS
* Broadband
* 4G/5G
* Dedicated circuits

---

# 5. Target WAN Architecture

The target WAN should support multiple transports and dynamically select the best path based on application requirements.

```text
                         +------------------+
                         | SD-WAN Controller |
                         +---------+--------+
                                   |
                    +--------------+--------------+
                    |                             |
                    v                             v
             +------+-------+              +------+-------+
             | Branch       |              | Data Center  |
             | SD-WAN Edge  |              | SD-WAN Edge  |
             +------+-------+              +------+-------+
                    |                             |
          +---------+---------+           +---------+---------+
          |                   |           |                   |
          v                   v           v                   v
       MPLS              Internet      Cloud              Internet
```

Target capabilities:

* Centralized policy
* Dynamic path selection
* Application-aware routing
* Secure overlay connectivity
* Cloud integration
* Automated provisioning
* Centralized assurance

---

# 6. WAN Architecture Gap

| Area                | Current State            | Target State         | Gap                        | Priority |
| ------------------- | ------------------------ | -------------------- | -------------------------- | -------- |
| WAN Architecture    | Traditional WAN          | SD-WAN               | Architecture modernization | High     |
| Connectivity        | Single/limited transport | Multi-transport      | Limited resilience         | High     |
| Routing             | Static/manual policy     | Centralized policy   | Operational gap            | High     |
| Application Routing | Limited                  | Application-aware    | Performance gap            | High     |
| Cloud Connectivity  | Manual                   | Integrated           | Cloud agility gap          | High     |
| Provisioning        | Manual                   | Zero-touch           | Automation gap             | High     |
| Visibility          | Device-focused           | End-to-end assurance | Monitoring gap             | High     |

---

# 7. WAN Transport Gap

## Current State

The current WAN may depend primarily on a single transport.

```text
Branch
  |
  v
MPLS
  |
  v
Data Center
```

## Target State

The target WAN should use multiple available transports.

```text
                 +----------------+
                 | SD-WAN Edge    |
                 +-------+--------+
                         |
             +-----------+-----------+
             |           |           |
             v           v           v
           MPLS       Internet     5G
```

## Identified Gaps

* Single transport dependency
* High circuit costs
* Limited path diversity
* Limited service-provider flexibility
* Limited resiliency

---

# 8. SD-WAN Gap Analysis

## Current State

```text
Engineer
   |
   v
WAN Device
   |
   v
Manual Configuration
   |
   v
Manual Troubleshooting
```

## Target State

```text
Network Administrator
          |
          v
SD-WAN Orchestrator
          |
          v
Centralized Policy
          |
          v
Automated Deployment
          |
          v
Centralized Assurance
```

Target capabilities:

* Centralized orchestration
* Zero-touch provisioning
* Template-based configuration
* Centralized policy
* Application-aware routing
* Automated monitoring

---

# 9. Application-Aware Routing Gap

## Current State

Traffic may use fixed routing paths.

```text
Application
     |
     v
Static Route
     |
     v
Primary WAN Link
```

## Target State

Routing decisions should consider application requirements.

```text
Application
     |
     v
Policy Evaluation
     |
     +--> Latency
     +--> Jitter
     +--> Packet Loss
     +--> Availability
     |
     v
Best Available Path
```

Example:

| Application       | Requirement        | Preferred Path |
| ----------------- | ------------------ | -------------- |
| Voice             | Low latency/jitter | Internet/MPLS  |
| Video             | High bandwidth     | Internet       |
| Business Critical | High reliability   | MPLS           |
| Guest Internet    | Direct Internet    | Local breakout |

---

# 10. WAN Routing Gap

| Routing Area         | Current State  | Target State      | Gap              |
| -------------------- | -------------- | ----------------- | ---------------- |
| Branch Routing       | To be assessed | Standardized      | Design gap       |
| WAN Routing          | To be assessed | Dynamic           | Automation gap   |
| BGP                  | To be assessed | Policy-driven     | Capability gap   |
| OSPF                 | To be assessed | Standardized      | Design gap       |
| Route Redistribution | To be assessed | Controlled        | Complexity gap   |
| Path Selection       | To be assessed | Application-aware | Intelligence gap |

---

# 11. Branch Connectivity Gap

## Current State

```text
New Branch
    |
    v
Circuit Installation
    |
    v
Manual Device Configuration
    |
    v
Manual Testing
```

## Target State

```text
New Branch
    |
    v
Connect WAN Circuits
    |
    v
Zero-Touch Provisioning
    |
    v
Centralized Policy
    |
    v
Automated Validation
```

## Identified Gaps

* Long deployment timelines
* Manual configuration
* Inconsistent branch standards
* Limited remote troubleshooting
* High operational effort

---

# 12. WAN High Availability Gap

Assess redundancy across the WAN.

| Component         | Current State  | Target State           | Gap                   |
| ----------------- | -------------- | ---------------------- | --------------------- |
| WAN Circuits      | To be assessed | Multi-transport        | Resilience gap        |
| Edge Devices      | To be assessed | HA pair                | Device redundancy gap |
| Service Providers | To be assessed | Multi-provider         | Provider dependency   |
| Routing           | To be assessed | Dynamic failover       | Recovery gap          |
| Data Center       | To be assessed | Redundant connectivity | Availability gap      |
| Cloud             | To be assessed | Multiple paths         | Connectivity gap      |

---

# 13. WAN Security Gap

## Current State

```text
Branch
  |
  v
WAN
  |
  v
Data Center Firewall
```

Security may primarily rely on centralized security controls.

## Target State

```text
Branch
  |
  v
Secure SD-WAN Overlay
  |
  +--> Encryption
  +--> Segmentation
  +--> Firewall
  +--> Security Policy
  |
  v
Enterprise / Cloud
```

Target capabilities:

* IPsec encryption
* Secure overlay tunnels
* Segmentation
* Integrated firewall
* Secure Internet breakout
* Centralized security policy

---

# 14. WAN Segmentation Gap

## Current State

Traffic may be separated using:

* VLANs
* Static VRFs
* ACLs
* Firewall zones

## Target State

```text
+-------------------------+
| Business Traffic        |
+-------------------------+
            |
            v
+-------------------------+
| Secure WAN Segmentation |
+-------------------------+
            |
     +------+------+
     |             |
     v             v
 Corporate       Guest
 Network         Network
```

Target capabilities:

* VRF segmentation
* Business-unit isolation
* Guest isolation
* IoT segmentation
* Security policy enforcement

---

# 15. Cloud Connectivity Gap

## Current State

```text
Enterprise
    |
    v
Data Center
    |
    v
Internet VPN
    |
    v
Cloud
```

## Target State

```text
                  +----------+
                  | AWS      |
                  +----+-----+
                       |
                  +----+-----+
                  | Azure    |
                  +----+-----+
                       |
                       v
                +------+------+
                | Cloud Edge  |
                +------+------+
                       |
                       v
                +------+------+
                | SD-WAN      |
                | Fabric      |
                +------+------+
                       |
                       v
                  Enterprise
```

Target capabilities:

* Direct cloud connectivity
* SD-WAN cloud integration
* Cloud route exchange
* Secure connectivity
* Centralized visibility

---

# 16. Internet Breakout Gap

## Current State

```text
Branch
  |
  v
WAN
  |
  v
Data Center
  |
  v
Internet
```

## Target State

```text
Branch
  |
  v
Security Policy
  |
  v
Local Internet Breakout
  |
  v
Cloud / SaaS / Internet
```

Benefits:

* Reduced backhauling
* Improved SaaS performance
* Reduced WAN bandwidth requirements
* Better application experience

Security requirements:

* Firewall
* Secure Web Gateway
* DNS security
* URL filtering
* Threat prevention

---

# 17. WAN Automation Gap

## Current State

```text
Change Request
      |
      v
Engineer
      |
      v
Manual CLI
      |
      v
Manual Validation
```

## Target State

```text
Configuration Template
          |
          v
Version Control
          |
          v
CI/CD Pipeline
          |
          v
Automated Validation
          |
          v
SD-WAN Deployment
```

Automation opportunities:

* Branch provisioning
* VPN creation
* Routing policy
* QoS policy
* Firewall policy
* Configuration compliance
* Software upgrades

---

# 18. WAN Observability Gap

## Current State

```text
WAN Device
    |
    v
SNMP / Syslog
    |
    v
Basic Monitoring
```

## Target State

```text
Application
     |
     v
Performance Metrics
     |
     +--> Latency
     +--> Jitter
     +--> Packet Loss
     +--> Availability
     |
     v
SD-WAN Analytics
     |
     v
Automated Policy / Remediation
```

Target visibility:

* Link health
* Application performance
* Path performance
* Tunnel health
* Device health
* Security events
* User experience

---

# 19. WAN Operations Gap

| Capability        | Current State | Target State        | Gap               |
| ----------------- | ------------- | ------------------- | ----------------- |
| Provisioning      | Manual        | Zero-touch          | Automation gap    |
| Routing           | Device-based  | Centralized policy  | Governance gap    |
| Troubleshooting   | CLI-based     | Analytics-based     | Visibility gap    |
| Failover          | Manual/static | Dynamic             | Resilience gap    |
| Monitoring        | Link-focused  | Application-focused | Observability gap |
| Change Management | Manual        | Automated workflow  | Process gap       |

---

# 20. WAN Technology Lifecycle Gap

| Technology         | Current State  | Target Requirement        | Gap               |
| ------------------ | -------------- | ------------------------- | ----------------- |
| MPLS               | To be assessed | Strategic/transition role | Cost optimization |
| Internet           | To be assessed | Secure transport          | Security gap      |
| Routers            | To be assessed | SD-WAN-compatible         | Platform gap      |
| VPN                | To be assessed | Automated overlay         | Operational gap   |
| Cloud Connectivity | To be assessed | Integrated connectivity   | Cloud gap         |

---

# 21. WAN Capability Gap Register

| ID      | Gap                           | Domain        | Impact | Priority | Recommendation                      |
| ------- | ----------------------------- | ------------- | ------ | -------- | ----------------------------------- |
| WAN-001 | Single transport dependency   | Connectivity  | High   | High     | Implement multi-transport WAN       |
| WAN-002 | Manual branch deployment      | Operations    | High   | High     | Implement zero-touch provisioning   |
| WAN-003 | Limited application awareness | Performance   | High   | High     | Implement application-aware routing |
| WAN-004 | Limited cloud integration     | Cloud         | High   | High     | Implement cloud-connected SD-WAN    |
| WAN-005 | Limited WAN visibility        | Observability | High   | High     | Implement WAN assurance             |
| WAN-006 | Static path selection         | Routing       | High   | High     | Implement dynamic policy            |
| WAN-007 | Manual VPN provisioning       | Security      | Medium | Medium   | Automate overlay deployment         |
| WAN-008 | High MPLS dependency          | Cost          | Medium | Medium   | Optimize transport strategy         |

---

# 22. WAN Transformation Roadmap

```text
Phase 1
Foundation
    |
    +--> WAN Inventory
    +--> Circuit Assessment
    +--> Application Assessment
    +--> IP Design
    |
    v
Phase 2
Resilience
    |
    +--> Secondary Links
    +--> Multi-Transport
    +--> HA Design
    |
    v
Phase 3
SD-WAN
    |
    +--> Controllers
    +--> Edge Devices
    +--> Overlay
    +--> Centralized Policy
    |
    v
Phase 4
Cloud Integration
    |
    +--> AWS
    +--> Azure
    +--> SaaS
    |
    v
Phase 5
Automation
    |
    +--> Templates
    +--> APIs
    +--> IaC
    +--> CI/CD
    |
    v
Phase 6
Optimization
    |
    +--> Analytics
    +--> Application Assurance
    +--> Automated Remediation
```

---

# 23. WAN Migration Dependencies

The transformation may depend on:

* Circuit availability
* SD-WAN platform selection
* Hardware compatibility
* IP addressing
* Routing design
* Security policy
* Cloud connectivity
* Application requirements
* Service-provider contracts
* Operations skills

---

# 24. WAN Transformation Risks

| Risk                      | Impact | Mitigation                        |
| ------------------------- | ------ | --------------------------------- |
| Circuit availability      | High   | Plan alternate transports         |
| Application disruption    | High   | Application dependency assessment |
| Routing errors            | High   | Lab testing and phased migration  |
| Security misconfiguration | High   | Security validation               |
| Provider dependency       | Medium | Multi-provider strategy           |
| Skills gap                | Medium | Training                          |
| Migration downtime        | High   | Parallel migration                |

---

# 25. Success Metrics

The WAN transformation should be measured using:

* WAN availability
* Application performance
* Link utilization
* Packet loss
* Latency
* Jitter
* Failover time
* Provisioning time
* Change success rate
* Automation coverage

Example target metrics:

```text
WAN Availability        > 99.9%
Automated Provisioning  > 80%
Successful Changes      > 95%
Failover Time           < 60 seconds
Critical App Visibility 100%
```

---

# 26. WAN Gap Analysis Summary

```text
+--------------------------+
| Traditional WAN          |
| MPLS / Manual / Static   |
+------------+-------------+
             |
             v
+------------+-------------+
| Transformation Gaps      |
|                          |
| Connectivity             |
| Routing                  |
| Cloud                    |
| Security                 |
| Automation               |
| Observability            |
+------------+-------------+
             |
             v
+------------+-------------+
| Target SD-WAN            |
| Secure / Dynamic         |
| Automated / Cloud-Ready  |
+--------------------------+
```

The major WAN transformation priorities are:

1. Introduce multi-transport connectivity.
2. Implement SD-WAN where business and technical requirements justify it.
3. Enable application-aware path selection.
4. Improve cloud and SaaS connectivity.
5. Automate branch provisioning.
6. Implement centralized WAN policy.
7. Improve WAN observability.
8. Establish secure local Internet breakout where appropriate.

---

## Conclusion

The WAN gap analysis defines the transformation required to move from a traditional, manually operated WAN to a modern, secure, resilient, application-aware, automated, and cloud-ready architecture.

The primary transformation is:

```text
Traditional WAN
      |
      v
MPLS-Centric
      |
      v
Static Routing
      |
      v
Manual Operations
      |
      v
Limited Visibility
```

to:

```text
Modern WAN
      |
      v
Multi-Transport SD-WAN
      |
      v
Application-Aware Routing
      |
      v
Centralized Policy
      |
      v
Automated Operations
      |
      v
End-to-End Observability
```

This document should be used as the foundation for the WAN transformation roadmap and implementation plan.

 automated, and assurance-driven wireless architecture.

