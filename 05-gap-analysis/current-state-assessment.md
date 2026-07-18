# Current-State Assessment

## 1. Purpose

This document establishes the current-state baseline of the enterprise network environment.

The assessment provides an objective view of the existing technology, architecture, security, operations, automation, monitoring, and skills capabilities.

This baseline is used as the foundation for identifying gaps between the current **As-Is State** and the target **To-Be Architecture**.

---

## 2. Assessment Scope

The current-state assessment covers:

- Campus LAN
- WAN connectivity
- Wireless infrastructure
- Network security
- Identity and access control
- Data center connectivity
- Cloud connectivity
- Network operations
- Automation
- Monitoring and observability
- ITSM processes
- Skills and capabilities
- Technology lifecycle

---

## 3. Current-State Assessment Framework

```text
+--------------------------+
| Current Enterprise       |
| Network Environment      |
+------------+-------------+
             |
             v
+------------+-------------+
| Technology Assessment    |
+--------------------------+
             |
             v
+--------------------------+
| Security Assessment      |
+--------------------------+
             |
             v
+--------------------------+
| Operations Assessment    |
+--------------------------+
             |
             v
+--------------------------+
| Automation Assessment    |
+--------------------------+
             |
             v
+--------------------------+
| Observability Assessment |
+--------------------------+
             |
             v
+--------------------------+
| Skills & Capability      |
+--------------------------+
````

---

# 4. Current-State Executive Summary

The current enterprise network environment should be assessed against the following dimensions:

| Domain         | Current Maturity | Key Observations                   |
| -------------- | ---------------- | ---------------------------------- |
| Campus Network | To be assessed   | Architecture and platform maturity |
| WAN            | To be assessed   | Connectivity and routing model     |
| Wireless       | To be assessed   | Coverage, capacity, and security   |
| Security       | To be assessed   | Identity and segmentation          |
| Automation     | To be assessed   | Manual versus automated operations |
| Observability  | To be assessed   | Monitoring and visibility          |
| Operations     | To be assessed   | Processes and service management   |
| Skills         | To be assessed   | Required technical capabilities    |

---

# 5. Campus Network Current State

## 5.1 Architecture

Document the current campus architecture.

Example:

```text
Users
  |
  v
Access Switches
  |
  v
Distribution Layer
  |
  v
Core Network
  |
  v
Data Center / WAN
```

Assess:

* Network topology
* Layer 2 design
* Layer 3 design
* Core architecture
* Distribution architecture
* Access architecture
* Spanning Tree design
* Routing protocols
* High availability

---

## 5.2 Current Campus Capabilities

| Capability        | Current State  | Maturity                        |
| ----------------- | -------------- | ------------------------------- |
| Layer 3 Access    | To be assessed | Basic / Intermediate / Advanced |
| VLAN Architecture | To be assessed | Basic / Intermediate / Advanced |
| Routing           | To be assessed | Basic / Intermediate / Advanced |
| High Availability | To be assessed | Basic / Intermediate / Advanced |
| Segmentation      | To be assessed | Basic / Intermediate / Advanced |
| Automation        | To be assessed | Basic / Intermediate / Advanced |

---

# 6. WAN Current State

## 6.1 WAN Architecture

Document the current WAN connectivity model.

```text
+---------+       +-------------+       +---------+
| Branch  |-------| WAN Network |-------|   DC    |
+---------+       +-------------+       +---------+
      |
      +---------------- Internet
```

Assess:

* MPLS connectivity
* Internet connectivity
* SD-WAN adoption
* WAN routing
* BGP
* OSPF
* IPsec
* Cloud connectivity
* WAN redundancy
* Traffic engineering

---

## 6.2 WAN Assessment

| Area               | Current State  | Key Limitation   |
| ------------------ | -------------- | ---------------- |
| Connectivity       | To be assessed | To be identified |
| Routing            | To be assessed | To be identified |
| Redundancy         | To be assessed | To be identified |
| Security           | To be assessed | To be identified |
| Cloud Connectivity | To be assessed | To be identified |
| Visibility         | To be assessed | To be identified |

---

# 7. Wireless Current State

Assess the current wireless infrastructure.

Key areas:

* Wireless controller architecture
* Access point technology
* Wi-Fi standards
* RF design
* Coverage
* Capacity
* Roaming
* Authentication
* Guest access
* Wireless security

Example:

```text
Wireless Client
      |
      v
Access Point
      |
      v
Wireless Controller
      |
      v
Enterprise Network
```

---

## 7.1 Wireless Assessment

| Capability          | Current State  | Gap Indicator             |
| ------------------- | -------------- | ------------------------- |
| Wi-Fi Standard      | To be assessed | Legacy / Modern           |
| Controller          | To be assessed | Centralized / Distributed |
| Authentication      | To be assessed | PSK / 802.1X              |
| RF Visibility       | To be assessed | Limited / Advanced        |
| Guest Access        | To be assessed | Available / Not Available |
| Wireless Monitoring | To be assessed | Basic / Advanced          |

---

# 8. Security Current State

Assess the current network security architecture.

Key areas:

* Identity and access control
* 802.1X
* MAB
* Cisco ISE
* RADIUS
* TACACS+
* Firewalls
* IDS/IPS
* Network segmentation
* Zero Trust
* Security monitoring

---

## 8.1 Current Security Model

```text
User / Device
      |
      v
Authentication
      |
      v
Network Access
      |
      v
VLAN-Based Policy
      |
      v
Firewall / ACL
```

Document whether access is primarily based on:

* IP address
* VLAN
* Subnet
* User identity
* Device identity
* Security Group Tags

---

## 8.2 Security Assessment

| Security Capability | Current State  | Maturity                        |
| ------------------- | -------------- | ------------------------------- |
| 802.1X              | To be assessed | Basic / Intermediate / Advanced |
| MAB                 | To be assessed | Basic / Intermediate / Advanced |
| ISE                 | To be assessed | Basic / Intermediate / Advanced |
| Segmentation        | To be assessed | Basic / Intermediate / Advanced |
| Firewall            | To be assessed | Basic / Intermediate / Advanced |
| Zero Trust          | To be assessed | Basic / Intermediate / Advanced |
| SIEM                | To be assessed | Basic / Intermediate / Advanced |

---

# 9. Identity and Access Management

Assess the current authentication and authorization architecture.

```text
User / Endpoint
       |
       v
Authentication
       |
       v
Identity Source
       |
       v
Authorization
       |
       v
Network Access
```

Document:

* Identity sources
* Active Directory integration
* RADIUS
* TACACS+
* 802.1X adoption
* MAB usage
* Endpoint profiling
* Guest authentication
* Administrative access

---

# 10. Network Segmentation Current State

Document how the network is currently segmented.

Possible segmentation mechanisms:

* VLANs
* VRFs
* Firewalls
* ACLs
* Security Group Tags

Example:

```text
Corporate Users
       |
       v
Corporate VLAN
       |
       v
Firewall / ACL
       |
       v
Applications
```

Assess:

* Macro-segmentation
* Micro-segmentation
* User-to-user isolation
* IoT isolation
* Guest isolation
* Server segmentation

---

# 11. Automation Current State

Assess the current level of network automation.

```text
Manual CLI
    |
    v
Scripts
    |
    v
Automation Tools
    |
    v
Infrastructure as Code
    |
    v
CI/CD
```

Document:

* Manual configuration processes
* Python usage
* Ansible usage
* Terraform usage
* API integration
* Git usage
* CI/CD adoption
* Configuration backups
* Compliance automation

---

## 11.1 Automation Assessment

| Capability | Current State  | Maturity                        |
| ---------- | -------------- | ------------------------------- |
| Python     | To be assessed | Basic / Intermediate / Advanced |
| Ansible    | To be assessed | Basic / Intermediate / Advanced |
| Terraform  | To be assessed | Basic / Intermediate / Advanced |
| APIs       | To be assessed | Basic / Intermediate / Advanced |
| Git        | To be assessed | Basic / Intermediate / Advanced |
| CI/CD      | To be assessed | Basic / Intermediate / Advanced |

---

# 12. Observability Current State

Assess current monitoring and visibility capabilities.

```text
Network Devices
      |
      v
SNMP / Syslog
      |
      v
Monitoring Platform
      |
      v
Operations Team
```

Assess:

* SNMP monitoring
* Syslog
* NetFlow
* Streaming telemetry
* Network assurance
* Application visibility
* Client visibility
* Event correlation
* Alerting
* ITSM integration

---

## 12.1 Observability Assessment

| Capability             | Current State  | Limitation       |
| ---------------------- | -------------- | ---------------- |
| Device Monitoring      | To be assessed | To be identified |
| Syslog                 | To be assessed | To be identified |
| NetFlow                | To be assessed | To be identified |
| Telemetry              | To be assessed | To be identified |
| Application Visibility | To be assessed | To be identified |
| Event Correlation      | To be assessed | To be identified |
| Automated Remediation  | To be assessed | To be identified |

---

# 13. Network Operations Current State

Assess current operational processes.

Key areas:

* Incident management
* Problem management
* Change management
* Configuration management
* Capacity management
* Availability management
* Documentation
* Disaster recovery

---

## 13.1 Operational Workflow

```text
Incident
   |
   v
Manual Investigation
   |
   v
Engineer Action
   |
   v
Resolution
   |
   v
Manual Documentation
```

Document:

* Average incident resolution time
* Escalation process
* Change approval process
* Standard operating procedures
* Operational ownership

---

# 14. ITSM Current State

Assess integration with IT service management platforms.

Key areas:

* Incident management
* Change management
* Problem management
* Configuration Management Database
* Service requests
* Asset management

Example:

```text
User
 |
 v
Service Desk
 |
 v
Network Operations
 |
 v
Engineering
```

---

# 15. Technology Lifecycle

Assess the lifecycle status of network technologies.

| Technology  | Current Version | Lifecycle Status      | Action        |
| ----------- | --------------- | --------------------- | ------------- |
| Switches    | To be assessed  | Current / Aging / EOL | To be defined |
| Routers     | To be assessed  | Current / Aging / EOL | To be defined |
| Wireless    | To be assessed  | Current / Aging / EOL | To be defined |
| Firewalls   | To be assessed  | Current / Aging / EOL | To be defined |
| Controllers | To be assessed  | Current / Aging / EOL | To be defined |

---

# 16. Skills and Capability Assessment

Assess the current technical capabilities required to operate the target architecture.

| Capability       | Current Level  | Required Level | Gap              |
| ---------------- | -------------- | -------------- | ---------------- |
| Routing          | To be assessed | Advanced       | To be identified |
| SD-Access        | To be assessed | Advanced       | To be identified |
| SD-WAN           | To be assessed | Advanced       | To be identified |
| Cisco ISE        | To be assessed | Advanced       | To be identified |
| Automation       | To be assessed | Advanced       | To be identified |
| Python           | To be assessed | Intermediate   | To be identified |
| Cloud Networking | To be assessed | Intermediate   | To be identified |

---

# 17. Current-State Maturity Model

Use the following maturity scale:

### Level 1 — Initial

* Highly manual
* Limited documentation
* Reactive operations

### Level 2 — Developing

* Basic standardization
* Some documented processes
* Limited automation

### Level 3 — Defined

* Standard processes
* Centralized monitoring
* Consistent architecture

### Level 4 — Managed

* Automation implemented
* Metrics-driven operations
* Proactive monitoring

### Level 5 — Optimized

* Intent-based operations
* Predictive analytics
* Continuous improvement

---

# 18. Current-State Maturity Assessment

| Domain        | Current Level  | Target Level |
| ------------- | -------------- | ------------ |
| Campus        | To be assessed | 4            |
| WAN           | To be assessed | 4            |
| Wireless      | To be assessed | 4            |
| Security      | To be assessed | 5            |
| Automation    | To be assessed | 4            |
| Observability | To be assessed | 5            |
| Operations    | To be assessed | 4            |

---

# 19. Key Current-State Findings

The assessment should identify the most important findings.

Example:

### Finding 1 — Legacy Network Architecture

The current environment relies heavily on traditional VLAN-based network segmentation and manual configuration.

### Finding 2 — Limited Identity-Based Access

Network access policies are not consistently based on user and device identity.

### Finding 3 — Limited Automation

Network provisioning and configuration changes require significant manual effort.

### Finding 4 — Limited End-to-End Visibility

Monitoring is primarily device-focused and provides limited application and user-experience visibility.

### Finding 5 — Skills Transformation Required

The target architecture requires additional capabilities in automation, cloud networking, security, and software-defined networking.

---

# 20. Current-State Constraints

Document constraints that may impact transformation.

Potential constraints:

* Legacy hardware
* Budget limitations
* Existing contracts
* Skills availability
* Business downtime requirements
* Regulatory requirements
* Application dependencies
* Vendor dependencies
* Migration complexity

---

# 21. Current-State Risks

| Risk                 | Impact | Likelihood | Mitigation              |
| -------------------- | ------ | ---------- | ----------------------- |
| Legacy hardware      | High   | Medium     | Technology refresh      |
| Manual operations    | High   | High       | Automation roadmap      |
| Limited segmentation | High   | Medium     | Zero Trust architecture |
| Skills shortage      | Medium | High       | Training and hiring     |
| Poor visibility      | High   | Medium     | Observability platform  |

---

# 22. Current-State Assessment Summary

```text
Current Environment
        |
        v
+-----------------------+
| Legacy Technology     |
+-----------------------+
        |
        v
+-----------------------+
| Manual Operations     |
+-----------------------+
        |
        v
+-----------------------+
| Limited Visibility    |
+-----------------------+
        |
        v
+-----------------------+
| Security Limitations  |
+-----------------------+
        |
        v
Transformation Required
```

---

# 23. Assessment Completion Checklist

* [ ] Campus architecture assessed
* [ ] WAN architecture assessed
* [ ] Wireless architecture assessed
* [ ] Security architecture assessed
* [ ] Identity architecture assessed
* [ ] Network segmentation assessed
* [ ] Automation maturity assessed
* [ ] Observability maturity assessed
* [ ] ITSM processes assessed
* [ ] Technology lifecycle assessed
* [ ] Skills assessed
* [ ] Current risks documented
* [ ] Current constraints documented
* [ ] Key findings documented

---

## Conclusion

This current-state assessment establishes the baseline for the Enterprise Network Transformation.

It provides the factual foundation required to compare the existing environment with the target architecture and identify the technology, security, operational, automation, observability, and capability gaps that must be addressed.

The findings from this document should be used as inputs to:

* `target-state-assessment.md`
* `network-gap-analysis.md`
* `security-gap-analysis.md`
* `automation-gap-analysis.md`
* `observability-gap-analysis.md`
* `transformation-roadmap.md`




