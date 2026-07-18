# Wireless Gap Analysis

## 1. Purpose

This document identifies the gaps between the current wireless network architecture and the target wireless architecture.

The analysis focuses on wireless coverage, capacity, RF design, authentication, security, roaming, automation, monitoring, and user experience.

The objective is to transform the wireless network from a traditional connectivity-focused WLAN into a secure, high-performance, identity-aware, and assurance-driven wireless platform.

---

## 2. Scope

This analysis covers:

- Wireless architecture
- Access points
- Wireless controllers
- Wi-Fi standards
- RF design
- Coverage
- Capacity
- Roaming
- Authentication
- Wireless security
- Guest access
- IoT connectivity
- Wireless automation
- Monitoring and assurance

---

# 3. Wireless Transformation Overview

```text
+--------------------------+
| Current Wireless        |
| Traditional WLAN        |
| Manual Operations       |
+------------+-------------+
             |
             v
+------------+-------------+
| Identified Gaps          |
|                          |
| Coverage                  |
| Capacity                 |
| Security                 |
| Authentication           |
| Visibility               |
| Automation               |
+------------+-------------+
             |
             v
+------------+-------------+
| Target Wireless          |
| Secure / High-Performance|
| Automated / Observable   |
+--------------------------+
````

---

# 4. Current Wireless Architecture

A traditional enterprise wireless architecture may consist of:

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
Campus Network
      |
      v
Data Center / Internet
```

Typical characteristics:

* Centralized wireless controllers
* VLAN-based SSIDs
* Static WLAN policies
* Manual AP deployment
* Limited client visibility
* PSK-based access for some devices
* Basic RF monitoring

---

# 5. Target Wireless Architecture

The target wireless architecture should provide:

* Wi-Fi 6/6E capability
* Identity-based access
* Dynamic policy enforcement
* High-density support
* Centralized assurance
* Automated provisioning
* Integrated security

```text
                         +------------------+
                         | Identity Source  |
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Cisco ISE        |
                         +--------+---------+
                                  |
                                  v
+----------------+      +--------+---------+
| Wireless Client|----->| Wi-Fi 6/6E AP    |
+----------------+      +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Wireless Platform|
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Policy-Based     |
                         | Enterprise Network|
                         +------------------+
```

---

# 6. Wireless Architecture Gap

| Area              | Current State        | Target State                | Gap                    | Priority |
| ----------------- | -------------------- | --------------------------- | ---------------------- | -------- |
| Wireless Platform | Traditional WLAN     | Modern Wi-Fi platform       | Platform modernization | High     |
| Authentication    | PSK / limited 802.1X | Identity-based              | Security gap           | High     |
| Segmentation      | VLAN-based           | Dynamic policy              | Segmentation gap       | High     |
| RF Management     | Manual/basic         | Automated optimization      | RF operations gap      | High     |
| Monitoring        | Device-focused       | Client experience assurance | Visibility gap         | High     |
| Provisioning      | Manual               | Automated                   | Automation gap         | Medium   |

---

# 7. Wireless Standards Gap

## Current State

The wireless environment may include a mixture of:

* Wi-Fi 4
* Wi-Fi 5
* Wi-Fi 6
* Legacy client devices

## Target State

The target environment should support:

* Wi-Fi 6
* Wi-Fi 6E where appropriate
* 5 GHz optimization
* 6 GHz deployment where supported
* WPA3 capability

| Area           | Current State  | Target State             | Gap               |
| -------------- | -------------- | ------------------------ | ----------------- |
| Wi-Fi Standard | To be assessed | Wi-Fi 6/6E               | Technology gap    |
| 5 GHz          | To be assessed | Optimized                | RF gap            |
| 6 GHz          | To be assessed | Available where suitable | Capability gap    |
| WPA3           | To be assessed | Supported                | Security gap      |
| Legacy Devices | To be assessed | Controlled support       | Compatibility gap |

---

# 8. RF Design Gap

## Current State

RF planning may depend on:

* Basic predictive surveys
* Manual channel selection
* Static transmit power
* Limited interference analysis

## Target State

```text
RF Design
    |
    v
Predictive Survey
    |
    v
AP-on-a-Stick Validation
    |
    v
Post-Deployment Survey
    |
    v
Continuous RF Assurance
```

Target capabilities:

* Predictive RF design
* Active validation
* Channel optimization
* Transmit power optimization
* Interference detection
* Capacity planning

---

# 9. Wireless Survey Gap

The target wireless design process should include:

```text
Requirements
     |
     v
Predictive Survey
     |
     v
AP-on-a-Stick Survey
     |
     v
Deployment
     |
     v
Validation Survey
     |
     v
Continuous Monitoring
```

Assess:

* Coverage
* Capacity
* Signal strength
* SNR
* Channel utilization
* Co-channel interference
* Adjacent-channel interference
* Roaming behavior

---

# 10. Coverage Gap

## Current State

Coverage may be designed primarily around signal strength.

## Target State

Wireless design should consider:

* Coverage
* Capacity
* Application requirements
* Client density
* Voice requirements
* Location services

Example:

| Requirement | Current State  | Target State        |
| ----------- | -------------- | ------------------- |
| Coverage    | To be assessed | Requirement-based   |
| RSSI        | To be assessed | Defined by use case |
| SNR         | To be assessed | Defined minimum     |
| Dead Zones  | To be assessed | Eliminated          |
| Roaming     | To be assessed | Validated           |

---

# 11. Capacity Gap

A network may have adequate coverage but insufficient capacity.

The target design should consider:

```text
Client Density
      |
      v
Application Usage
      |
      v
Channel Availability
      |
      v
AP Capacity
      |
      v
Capacity Design
```

Assess:

* Number of clients per AP
* Concurrent users
* High-density areas
* Application traffic
* Voice/video traffic
* Channel utilization

---

# 12. 2.4 GHz and 5 GHz Gap

## Current State

The wireless environment may rely heavily on 2.4 GHz.

## Target State

The design should prioritize:

```text
2.4 GHz
   |
   +--> Legacy / IoT Use
   |
   v
5 GHz
   |
   +--> Primary Enterprise Capacity
   |
   v
6 GHz
   |
   +--> New High-Capacity Devices
```

Key considerations:

* 2.4 GHz has fewer non-overlapping channels
* 5 GHz provides greater capacity
* 6 GHz provides additional spectrum where supported
* Client capability must be considered

---

# 13. Wireless Authentication Gap

## Current State

Authentication may include:

* Shared PSK
* Open guest access
* Limited 802.1X
* Static VLAN assignment

## Target State

```text
Client
  |
  v
802.1X / MAB
  |
  v
Cisco ISE
  |
  +--> Authentication
  +--> Device Profiling
  +--> Authorization
  +--> SGT Assignment
  |
  v
Dynamic Network Access
```

Target capabilities:

* 802.1X
* EAP authentication
* MAB for non-802.1X devices
* Device profiling
* Dynamic authorization
* Certificate-based authentication where appropriate

---

# 14. Wireless Security Gap

| Security Area  | Current State  | Target State         | Gap              |
| -------------- | -------------- | -------------------- | ---------------- |
| Authentication | PSK            | 802.1X               | Identity gap     |
| Encryption     | To be assessed | WPA2/WPA3            | Security gap     |
| Guest Access   | VLAN-based     | Isolated policy      | Segmentation gap |
| IoT            | Static access  | Profile-based policy | Device gap       |
| Access Control | Static         | Dynamic              | Policy gap       |
| Visibility     | Limited        | Identity-aware       | Monitoring gap   |

---

# 15. SSID Architecture Gap

## Current State

Organizations may have too many SSIDs.

```text
SSID 1
SSID 2
SSID 3
SSID 4
SSID 5
SSID 6
```

## Target State

The target architecture should minimize SSID proliferation.

Example:

```text
Corporate SSID
      |
      v
Identity-Based Policy
      |
      +--> Employee
      +--> Contractor
      +--> IoT
```

Additional SSIDs should exist only when there is a valid technical or business requirement.

---

# 16. Wireless Segmentation Gap

## Current State

```text
SSID
  |
  v
VLAN
  |
  v
ACL
```

## Target State

```text
User / Device Identity
          |
          v
      ISE Policy
          |
          v
   Dynamic Authorization
          |
          v
      SGT / VRF
          |
          v
    Policy Enforcement
```

The key transformation is from SSID-based segmentation to identity-based segmentation.

---

# 17. Guest Wireless Gap

## Current State

```text
Guest
  |
  v
Guest SSID
  |
  v
Guest VLAN
  |
  v
Internet
```

## Target State

```text
Guest
  |
  v
Guest Authentication
  |
  v
Guest Policy
  |
  v
Isolated Network
  |
  v
Internet Only
```

Target capabilities:

* Guest portal
* Internet-only access
* Client isolation
* Time-based access
* Centralized policy
* Monitoring

---

# 18. IoT Wireless Gap

IoT devices often do not support 802.1X.

## Current State

```text
IoT Device
    |
    v
Shared PSK
    |
    v
VLAN
```

## Target State

```text
IoT Device
    |
    v
MAB / Profiling
    |
    v
Cisco ISE
    |
    v
Dynamic Policy
    |
    v
Restricted Access
```

Target controls:

* Device profiling
* MAB
* Restricted communication
* Dedicated policy
* Monitoring

---

# 19. Wireless Roaming Gap

Assess roaming performance across the wireless environment.

Key areas:

* Layer 2 roaming
* Layer 3 roaming
* 802.11k
* 802.11v
* 802.11r
* Fast roaming
* Voice roaming

Target requirements:

* Seamless roaming
* Consistent authentication
* Low packet loss
* Application continuity

---

# 20. Wireless Controller Gap

| Capability    | Current State  | Target State      | Gap              |
| ------------- | -------------- | ----------------- | ---------------- |
| Controller    | To be assessed | HA architecture   | Availability gap |
| AP Management | Manual         | Centralized       | Operational gap  |
| RF Management | Basic          | Automated         | Optimization gap |
| Policy        | Static         | Identity-based    | Security gap     |
| Assurance     | Limited        | Client experience | Visibility gap   |

---

# 21. Wireless Automation Gap

## Current State

```text
New AP
  |
  v
Manual Configuration
  |
  v
Manual Deployment
  |
  v
Manual Validation
```

## Target State

```text
New AP
  |
  v
Automated Discovery
  |
  v
Zero-Touch Provisioning
  |
  v
Policy Assignment
  |
  v
Automated Validation
```

Automation opportunities:

* AP onboarding
* Configuration
* RF profiles
* SSID deployment
* Policy assignment
* Software upgrades
* Compliance validation

---

# 22. Wireless Observability Gap

## Current State

```text
AP
 |
 v
SNMP
 |
 v
Basic Monitoring
```

## Target State

```text
Client
  |
  +--> Signal
  +--> SNR
  +--> Roaming
  +--> Authentication
  +--> Application Experience
  |
  v
Wireless Assurance
  |
  v
Analytics / Alerting
```

Target visibility:

* Client health
* AP health
* RF health
* Authentication failures
* Roaming issues
* Application experience
* Interference

---

# 23. Wireless Operations Gap

| Capability      | Current State  | Target State          |
| --------------- | -------------- | --------------------- |
| AP Deployment   | Manual         | Automated             |
| RF Management   | Reactive       | Proactive             |
| Troubleshooting | CLI-based      | Analytics-based       |
| Authentication  | Static         | Dynamic               |
| Monitoring      | Device-focused | Client-focused        |
| Changes         | Manual         | Controlled automation |

---

# 24. Wireless Technology Lifecycle Gap

| Technology     | Current State  | Target Requirement             | Gap            |
| -------------- | -------------- | ------------------------------ | -------------- |
| Access Points  | To be assessed | Wi-Fi 6/6E                     | Platform gap   |
| Controllers    | To be assessed | Supported HA platform          | Lifecycle gap  |
| Authentication | To be assessed | 802.1X                         | Security gap   |
| RF Tools       | To be assessed | Professional survey capability | Design gap     |
| Monitoring     | To be assessed | Assurance platform             | Visibility gap |

---

# 25. Wireless Capability Gap Register

| ID       | Gap                            | Domain      | Impact | Priority | Recommendation                    |
| -------- | ------------------------------ | ----------- | ------ | -------- | --------------------------------- |
| WLAN-001 | Legacy wireless infrastructure | Technology  | High   | High     | Modernize AP platform             |
| WLAN-002 | Limited 802.1X adoption        | Security    | High   | High     | Implement identity-based access   |
| WLAN-003 | Excessive SSIDs                | Design      | Medium | Medium   | Simplify SSID architecture        |
| WLAN-004 | Static VLAN segmentation       | Security    | High   | High     | Implement dynamic policy          |
| WLAN-005 | Limited RF visibility          | Operations  | High   | High     | Implement wireless assurance      |
| WLAN-006 | Manual AP deployment           | Automation  | Medium | Medium   | Implement zero-touch provisioning |
| WLAN-007 | Limited capacity planning      | Performance | High   | High     | Perform capacity-based design     |
| WLAN-008 | Limited guest isolation        | Security    | High   | High     | Implement isolated guest access   |

---

# 26. Wireless Transformation Roadmap

```text
Phase 1
Assessment
    |
    +--> Site Survey
    +--> RF Assessment
    +--> Capacity Assessment
    +--> Client Assessment
    |
    v
Phase 2
Foundation
    |
    +--> Platform Readiness
    +--> IP Design
    +--> Controller HA
    |
    v
Phase 3
Security
    |
    +--> 802.1X
    +--> ISE
    +--> MAB
    +--> Profiling
    |
    v
Phase 4
Optimization
    |
    +--> Wi-Fi 6/6E
    +--> RF Optimization
    +--> Capacity Design
    |
    v
Phase 5
Automation
    |
    +--> AP Provisioning
    +--> Policy Automation
    +--> APIs
    |
    v
Phase 6
Assurance
    |
    +--> Client Health
    +--> RF Analytics
    +--> Application Visibility
```

---

# 27. Wireless Migration Dependencies

The transformation may depend on:

* RF survey
* AP hardware compatibility
* Controller platform
* ISE integration
* Identity infrastructure
* Client compatibility
* Application requirements
* Cabling and PoE
* Switch capacity
* Power availability
* Operations skills

---

# 28. Wireless Transformation Risks

| Risk                            | Impact | Mitigation                 |
| ------------------------------- | ------ | -------------------------- |
| Inadequate RF design            | High   | Professional survey        |
| Legacy clients                  | Medium | Compatibility assessment   |
| Authentication failure          | High   | Pilot 802.1X               |
| Insufficient PoE                | High   | Switch capacity assessment |
| High-density performance issues | High   | Capacity planning          |
| Roaming issues                  | Medium | Application testing        |
| Poor AP placement               | High   | Validation survey          |

---

# 29. Success Metrics

The wireless transformation should be measured using:

* Coverage
* Capacity
* Client health
* Authentication success rate
* Roaming success
* Application performance
* RF utilization
* Interference
* AP availability
* User experience

Example target metrics:

```text
Authentication Success Rate  > 98%
AP Availability              > 99.9%
Coverage Compliance          > 95%
Client Health                > 95%
Critical Area Coverage       100%
```

---

# 30. Wireless Gap Analysis Summary

```text
+--------------------------+
| Traditional WLAN         |
| Static / Manual / VLAN   |
+------------+-------------+
             |
             v
+------------+-------------+
| Transformation Gaps      |
|                          |
| RF Design                |
| Capacity                |
| Authentication          |
| Security                |
| Automation              |
| Observability            |
+------------+-------------+
             |
             v
+------------+-------------+
| Target Wireless          |
| Wi-Fi 6/6E              |
| Identity-Based           |
| Automated / Assured      |
+--------------------------+
```

The major wireless transformation priorities are:

1. Modernize wireless infrastructure.
2. Design based on both coverage and capacity.
3. Implement identity-based authentication.
4. Integrate Cisco ISE.
5. Reduce unnecessary SSIDs.
6. Implement dynamic segmentation.
7. Improve RF and client visibility.
8. Automate AP provisioning and policy deployment.

---

## Conclusion

The wireless gap analysis defines the transformation required to move from a traditional WLAN to a modern, secure, high-performance, identity-aware, and assurance-driven wireless architecture.

The primary transformation is:

```text
Traditional WLAN
      |
      v
Static SSIDs
      |
      v
VLAN-Based Access
      |
      v
Manual RF Operations
      |
      v
Limited Visibility
```

to:

```text
Modern Wireless
      |
      v
Wi-Fi 6/6E
      |
      v
Identity-Based Access
      |
      v
Dynamic Policy
      |
      v
Automated RF Optimization
      |
      v
Client Experience Assurance
```

This document should be used as the foundation for the wireless transformation roadmap and implementation plan.



