# Target-State Assessment

## 1. Purpose

This document defines the target-state capabilities required to achieve the Enterprise Network Transformation vision.

The target state represents the desired future architecture, technology, security, automation, observability, and operational capabilities.

It provides the reference point for identifying gaps between the current **As-Is State** and the target **To-Be State**.

---

## 2. Target-State Vision

The target enterprise network will be:

- Secure by design
- Identity-aware
- Highly available
- Automated
- Observable
- Scalable
- Cloud-ready
- Policy-driven
- Standards-based
- Operationally efficient

```text
+------------------------------------------------+
|          Enterprise Network Transformation      |
+------------------------------------------------+
                        |
        +---------------+---------------+
        |               |               |
        v               v               v
   Secure Network   Automated Network  Observable
                                      Network
        |               |               |
        +---------------+---------------+
                        |
                        v
              Business-Aligned Network
````

---

# 3. Target-State Architecture

```text
                         +-------------------+
                         | Business Services  |
                         +---------+---------+
                                   |
                                   v
                         +---------+---------+
                         | Applications      |
                         +---------+---------+
                                   |
                                   v
                  +----------------+----------------+
                  |                                 |
                  v                                 v
           Secure Connectivity                Cloud Connectivity
                  |                                 |
                  +----------------+----------------+
                                   |
                                   v
                         +---------+---------+
                         | Enterprise WAN   |
                         | SD-WAN / Internet|
                         +---------+---------+
                                   |
                                   v
                         +---------+---------+
                         | Campus / Branch  |
                         | SD-Access        |
                         +---------+---------+
                                   |
                  +----------------+----------------+
                  |                                 |
                  v                                 v
             Identity & Security              Wireless
             Cisco ISE / SGT                  Wi-Fi 6/6E
                  |                                 |
                  +----------------+----------------+
                                   |
                                   v
                         +---------+---------+
                         | Automation & IaC |
                         | Python / Ansible |
                         | Terraform / CI/CD|
                         +---------+---------+
                                   |
                                   v
                         +---------+---------+
                         | Observability    |
                         | Telemetry / SIEM |
                         +-------------------+
```

---

# 4. Target-State Capability Model

The target state is defined across the following capabilities:

| Domain        | Target Capability                            |
| ------------- | -------------------------------------------- |
| Campus        | Scalable and resilient campus architecture   |
| WAN           | SD-WAN and intelligent path selection        |
| Wireless      | Wi-Fi 6/6E with centralized assurance        |
| Security      | Zero Trust and identity-based access         |
| Identity      | Centralized authentication and authorization |
| Segmentation  | VRF and identity-based segmentation          |
| Automation    | Infrastructure as Code and CI/CD             |
| Observability | End-to-end telemetry and analytics           |
| Operations    | Proactive and automated operations           |
| Cloud         | Secure hybrid-cloud connectivity             |

---

# 5. Target Campus Architecture

The target campus architecture should provide:

* Scalable Layer 3 design
* Resilient core infrastructure
* Reduced Layer 2 dependency
* Identity-based access
* Policy-driven segmentation
* Centralized orchestration

```text
Users / Devices
       |
       v
Fabric Edge
       |
       v
SD-Access Fabric
       |
       +--> Control Plane
       |
       +--> Border Node
       |
       v
Enterprise / Data Center / Cloud
```

### Target Capabilities

* Cisco SD-Access
* Catalyst Center
* Fabric Edge Nodes
* Control Plane Nodes
* Border Nodes
* Virtual Networks
* Scalable Groups

---

# 6. Target WAN Architecture

The target WAN architecture should provide:

* Application-aware routing
* Dynamic path selection
* Secure connectivity
* Internet and MPLS integration
* Cloud connectivity
* Centralized policy management

```text
                 +-------------+
                 | SD-WAN      |
                 | Controller  |
                 +------+------+
                        |
        +---------------+---------------+
        |                               |
        v                               v
     Branch                         Data Center
        |                               |
        +---------------+---------------+
                        |
                        v
                      Cloud
```

### Target Capabilities

* SD-WAN
* BGP
* OSPF
* IPsec
* Application-aware routing
* Centralized policy
* Multi-transport connectivity

---

# 7. Target Wireless Architecture

The target wireless environment should provide:

* Wi-Fi 6/6E capability
* High-density support
* Centralized management
* Secure authentication
* RF optimization
* Client experience monitoring

```text
Wireless Client
      |
      v
Wi-Fi 6/6E AP
      |
      v
Wireless Platform
      |
      v
Identity / Policy
      |
      v
Enterprise Network
```

### Target Capabilities

* 802.1X
* WPA3 where applicable
* Centralized RF management
* Wireless assurance
* Guest network isolation
* Automated provisioning

---

# 8. Target Security Architecture

The target security model follows a Zero Trust approach.

```text
User / Device
      |
      v
Identity Verification
      |
      v
Device Assessment
      |
      v
Policy Evaluation
      |
      v
Access Decision
      |
      v
Continuous Monitoring
```

### Target Capabilities

* Zero Trust
* 802.1X
* Cisco ISE
* MAB for non-802.1X devices
* Endpoint profiling
* Security Group Tags
* Dynamic authorization
* Network segmentation
* SIEM integration

---

# 9. Target Identity Architecture

```text
User / Endpoint
       |
       v
+------+-------+
| Identity     |
| Source       |
+------+-------+
       |
       v
+------+-------+
| Cisco ISE    |
+------+-------+
       |
       v
Authentication
       |
       v
Authorization
       |
       v
Dynamic Policy
```

The target identity architecture should support:

* Centralized authentication
* Role-based access
* Device profiling
* Dynamic authorization
* Guest access
* Administrative access control

---

# 10. Target Segmentation Architecture

The target architecture should move from static VLAN-based segmentation toward identity-based policy enforcement.

```text
+----------------+
| User Identity  |
+--------+-------+
         |
         v
+--------+-------+
| Device Context |
+--------+-------+
         |
         v
+--------+-------+
| Policy         |
+--------+-------+
         |
         v
+--------+-------+
| SGT / VRF      |
+--------+-------+
         |
         v
+--------+-------+
| Enforcement    |
+----------------+
```

Target segmentation mechanisms:

* VRFs
* Security Group Tags
* Firewall policies
* ACLs
* Identity-based policies

---

# 11. Target Automation Architecture

The target operating model follows a NetDevOps approach.

```text
Engineer
   |
   v
Git Repository
   |
   v
Pull Request
   |
   v
CI/CD Pipeline
   |
   v
Testing
   |
   v
Approval
   |
   v
Automation
   |
   v
Network Infrastructure
```

### Target Technologies

* Python
* Ansible
* Terraform
* Jinja2
* GitHub
* GitHub Actions
* REST APIs
* Infrastructure as Code

---

# 12. Target Infrastructure as Code Model

```text
Desired State
      |
      v
Code Repository
      |
      v
Validation
      |
      v
Peer Review
      |
      v
Deployment
      |
      v
Actual Infrastructure
```

The target model should provide:

* Repeatability
* Version control
* Automated testing
* Peer review
* Auditability
* Rollback

---

# 13. Target Observability Architecture

The target observability platform should provide end-to-end visibility.

```text
Network Infrastructure
        |
        +--> Metrics
        +--> Logs
        +--> Events
        +--> Flow Data
        +--> Telemetry
        |
        v
Observability Platform
        |
        +--> Dashboards
        +--> Analytics
        +--> Alerting
        +--> Correlation
        |
        v
ITSM / SIEM / Automation
```

### Target Capabilities

* Streaming telemetry
* SNMPv3
* Syslog
* NetFlow/IPFIX
* Network assurance
* Application visibility
* Event correlation
* Automated remediation

---

# 14. Target Operations Model

The target operations model should move from reactive operations to proactive service management.

```text
Monitor
   |
   v
Detect
   |
   v
Analyze
   |
   v
Automate
   |
   v
Remediate
   |
   v
Validate
   |
   v
Improve
```

Target capabilities:

* Proactive monitoring
* Automated incident detection
* Root-cause analysis
* Automated remediation
* Service-level monitoring
* Continuous improvement

---

# 15. Target ITSM Integration

```text
Monitoring
    |
    v
Event Correlation
    |
    v
ServiceNow
    |
    v
Incident / Change
    |
    v
Automation
    |
    v
Validation
```

The target model should support:

* Automated incident creation
* Change approval
* Automated implementation
* Post-change validation
* Audit trails

---

# 16. Target Cloud Connectivity

The target architecture should support secure hybrid-cloud connectivity.

```text
Enterprise Network
        |
        v
Cloud Connectivity
        |
        +--> AWS
        +--> Azure
        +--> SaaS
        |
        v
Cloud Security
```

Target capabilities:

* Direct cloud connectivity
* IPsec VPN
* SD-WAN cloud integration
* Cloud routing
* Secure access
* Centralized visibility

---

# 17. Target Resilience Model

Critical network services should be designed without single points of failure.

```text
                 +----------------+
                 | Primary Path   |
                 +--------+-------+
                          |
                     Network Service
                          |
                 +--------+-------+
                 | Secondary Path |
                 +----------------+
```

Resilience should be implemented through:

* Device redundancy
* Link redundancy
* Routing redundancy
* Controller redundancy
* Data center redundancy
* Geographic redundancy where required

---

# 18. Target Technology Maturity

| Domain        | Current        | Target  |
| ------------- | -------------- | ------- |
| Campus        | To be assessed | Level 4 |
| WAN           | To be assessed | Level 4 |
| Wireless      | To be assessed | Level 4 |
| Security      | To be assessed | Level 5 |
| Automation    | To be assessed | Level 4 |
| Observability | To be assessed | Level 5 |
| Operations    | To be assessed | Level 4 |

### Maturity Levels

```text
Level 1: Manual
    |
    v
Level 2: Developing
    |
    v
Level 3: Defined
    |
    v
Level 4: Managed
    |
    v
Level 5: Optimized
```

---

# 19. Target-State Requirements

## Technology

* [ ] Scalable network architecture
* [ ] Modern network platforms
* [ ] SD-Access capability
* [ ] SD-WAN capability
* [ ] Wi-Fi 6/6E capability
* [ ] Cloud connectivity

## Security

* [ ] Zero Trust principles
* [ ] Identity-based access
* [ ] 802.1X
* [ ] Cisco ISE
* [ ] Dynamic segmentation
* [ ] SIEM integration

## Automation

* [ ] Git-based workflows
* [ ] Infrastructure as Code
* [ ] Ansible automation
* [ ] Python automation
* [ ] CI/CD pipelines
* [ ] Automated validation

## Observability

* [ ] Metrics collection
* [ ] Centralized logging
* [ ] Streaming telemetry
* [ ] Flow visibility
* [ ] Event correlation
* [ ] Automated remediation

## Operations

* [ ] Standardized processes
* [ ] ITSM integration
* [ ] Service-level monitoring
* [ ] Proactive operations
* [ ] Continuous improvement

---

# 20. Target-State Success Metrics

| Area              | Target Metric                    |
| ----------------- | -------------------------------- |
| Availability      | ≥ 99.9% for critical services    |
| Change Success    | > 95% successful changes         |
| Automation        | > 60% repeatable tasks automated |
| Incident Response | Reduced MTTR                     |
| Security          | Increased identity-based access  |
| Visibility        | End-to-end service monitoring    |
| Compliance        | Automated policy validation      |

---

# 21. Target-State Benefits

The target architecture will provide:

* Improved network resilience
* Better security posture
* Reduced manual operations
* Faster service delivery
* Improved troubleshooting
* Better user experience
* Reduced configuration errors
* Improved compliance
* Increased operational efficiency

---

# 22. Target-State Assessment Summary

```text
Current State
      |
      v
Transformation
      |
      +--> Modern Network Architecture
      |
      +--> Zero Trust Security
      |
      +--> Network Automation
      |
      +--> Full Observability
      |
      +--> Proactive Operations
      |
      v
Target Enterprise Network
```

---

# 23. Relationship with Gap Analysis

The target-state assessment defines the future capabilities required by the enterprise.

```text
Current-State Assessment
          |
          v
       AS-IS
          |
          +--------+
                   |
                   v
            Gap Analysis
                   ^
                   |
          +--------+
          |
          v
Target-State Assessment
          |
          v
       TO-BE
```

The gap between the current and target states becomes the input for:

* `network-gap-analysis.md`
* `campus-gap-analysis.md`
* `wan-gap-analysis.md`
* `wireless-gap-analysis.md`
* `security-gap-analysis.md`
* `automation-gap-analysis.md`
* `observability-gap-analysis.md`

---

# 24. Conclusion

The target-state assessment defines the future capabilities required to achieve the Enterprise Network Transformation vision.

The target environment is designed to be:

* Secure
* Resilient
* Scalable
* Identity-aware
* Automated
* Observable
* Cloud-ready
* Policy-driven

This document serves as the baseline for comparing the current environment against the desired future state and creating the detailed gap analysis and transformation roadmap.



