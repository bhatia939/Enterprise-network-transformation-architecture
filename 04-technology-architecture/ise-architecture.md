# Cisco ISE Architecture

## 1. Purpose

This document defines the Cisco Identity Services Engine (ISE) architecture supporting the Enterprise Network Transformation.

Cisco ISE provides centralized identity, authentication, authorization, endpoint profiling, policy enforcement, and security policy integration across wired, wireless, and VPN access environments.

---

## 2. Architecture Objectives

The ISE architecture aims to:

- Provide centralized identity-based access control.
- Authenticate users and devices.
- Support 802.1X and MAB authentication.
- Profile unknown endpoints.
- Apply dynamic authorization policies.
- Integrate with Cisco SD-Access.
- Support Security Group Tags (SGTs).
- Provide high availability.
- Improve security visibility and compliance.

---

## 3. ISE Architecture Overview

```text
                         Users / Devices
                                |
                 +--------------+--------------+
                 |                             |
             Wired Access                 Wireless Access
                 |                             |
                 +--------------+--------------+
                                |
                         Network Devices
                                |
                           RADIUS / TACACS+
                                |
                 +--------------+--------------+
                 |                             |
          +------+-------+             +-------+------+
          |   ISE Node 1 |             |   ISE Node 2 |
          |  PAN / PSN   |             |  PAN / PSN   |
          +------+-------+             +-------+------+
                 |                             |
                 +--------------+--------------+
                                |
                        Identity Directory
````

---

## 4. ISE Node Roles

Cisco ISE deployments use different node personas.

### 4.1 Policy Administration Node (PAN)

The PAN provides centralized policy administration.

Responsibilities:

* Policy configuration
* System administration
* Policy management
* Configuration replication

---

### 4.2 Policy Service Node (PSN)

The PSN processes authentication and authorization requests.

Responsibilities:

* RADIUS authentication
* TACACS+ authentication
* 802.1X processing
* MAB processing
* Guest services
* Profiling
* Authorization

---

### 4.3 Monitoring and Troubleshooting Node (MnT)

The MnT node provides:

* Monitoring
* Reporting
* Troubleshooting
* Authentication logs
* Operational dashboards

---

## 5. Recommended High-Availability Architecture

```text
                    +-------------------+
                    |   Administration  |
                    |      PAN-1        |
                    +---------+---------+
                              |
                      Configuration Sync
                              |
                    +---------+---------+
                    |   Administration  |
                    |      PAN-2        |
                    +-------------------+

        +-------------------+   +-------------------+
        |       PSN-1       |   |       PSN-2       |
        | Authentication    |   | Authentication    |
        +---------+---------+   +---------+---------+
                  |                       |
                  +-----------+-----------+
                              |
                         Network Devices
```

### High Availability Principles

* Deploy redundant PSNs.
* Distribute authentication load.
* Avoid a single authentication point.
* Use redundant PAN and MnT services where required.
* Ensure network devices have multiple RADIUS servers configured.

---

## 6. Authentication Architecture

### 6.1 802.1X Authentication

```text
+----------+        +-------------+        +---------+
| Supplicant|       | Authenticator|        |   ISE   |
| Endpoint  |       | Switch / AP  |        |         |
+----+------+        +------+------+        +----+----+
     |                      |                    |
     | EAP                  | RADIUS             |
     +--------------------->+------------------->|
                            |                    |
                            | Authentication     |
                            |<-------------------+
                            |
                       Network Access
```

### Authentication Flow

1. Endpoint connects to the network.
2. The access device detects the endpoint.
3. 802.1X authentication starts.
4. The access device sends a RADIUS request to ISE.
5. ISE validates the identity.
6. ISE evaluates authorization policy.
7. Access is permitted, restricted, or denied.

---

## 7. MAB Authentication

MAB supports devices that cannot perform 802.1X authentication.

### Example Devices

* Printers
* IoT devices
* IP phones
* Legacy devices
* Building management systems

```text
Endpoint
   |
   v
Network Device
   |
   | MAC Address
   v
Cisco ISE
   |
   v
MAC Database / Profiling
   |
   v
Authorization Policy
```

---

## 8. Identity Sources

ISE may integrate with:

* Active Directory
* LDAP
* Internal users
* Certificate Authority
* External identity providers

```text
                  +----------------+
                  | Active Directory|
                  +--------+-------+
                           |
                           | LDAP / Kerberos
                           v
+----------+       +-------+-------+
| Endpoint |------>|     Cisco ISE |
+----------+       +-------+-------+
                           |
                           v
                    Authorization
```

---

## 9. Endpoint Profiling

ISE identifies endpoints based on multiple attributes.

### Profiling Inputs

* MAC address
* DHCP information
* HTTP information
* CDP / LLDP
* RADIUS attributes
* Network behavior

### Example Endpoint Types

| Endpoint         | Example Policy               |
| ---------------- | ---------------------------- |
| Corporate Laptop | Corporate access             |
| Printer          | Restricted printer access    |
| IP Phone         | Voice access                 |
| IoT Device       | Restricted IoT access        |
| Unknown Device   | Limited or quarantine access |

---

## 10. Authorization Architecture

Authorization policies determine what access an authenticated endpoint receives.

```text
Identity
   +
Device Type
   +
Location
   +
Security Posture
   |
   v
Authorization Policy
   |
   +--> Permit
   |
   +--> Restrict
   |
   +--> Quarantine
   |
   +--> Deny
```

### Authorization Results May Include

* VLAN assignment
* Security Group Tag
* Downloadable ACL
* URL redirect
* Session timeout
* Access restriction

---

## 11. Policy Architecture

```text
+--------------------------+
| Authentication Policy    |
+------------+-------------+
             |
             v
+--------------------------+
| Identity Validation      |
+------------+-------------+
             |
             v
+--------------------------+
| Authorization Policy    |
+------------+-------------+
             |
             v
+--------------------------+
| Authorization Result    |
+--------------------------+
```

---

## 12. Cisco ISE and SDA Integration

```text
                    +----------------+
                    | Catalyst Center|
                    +--------+-------+
                             |
                             |
                    +--------+-------+
                    |   Cisco ISE    |
                    +--------+-------+
                             |
                    Identity / Policy
                             |
                    +--------+-------+
                    |  SDA Fabric    |
                    +----------------+
```

ISE provides:

* Identity information
* Authentication
* Authorization
* Endpoint profiling
* Security Group Tag assignment
* Policy integration

---

## 13. Security Group Tags

Security Group Tags enable identity-based policy enforcement.

```text
User / Device
      |
      v
Cisco ISE
      |
      v
SGT Assignment
      |
      v
Network Fabric
      |
      v
SGT-Based Policy
```

### Example

| Endpoint   | SGT        |
| ---------- | ---------- |
| Employee   | Employee   |
| Contractor | Contractor |
| IoT Device | IoT        |
| Guest      | Guest      |
| Server     | Server     |

---

## 14. SGT Policy Model

```text
Source SGT        Destination SGT        Action
------------------------------------------------
Employee    --->  Application            Permit
Guest       --->  Internal Server        Deny
IoT         --->  Approved Service       Permit
Contractor  --->  Sensitive Server       Deny
Admin       --->  Network Device         Permit
```

---

## 15. TACACS+ Architecture

ISE can provide centralized administrative access control for network devices.

```text
Network Administrator
          |
          v
Network Device
          |
          | TACACS+
          v
       Cisco ISE
          |
          v
Authentication / Authorization
```

### Capabilities

* Centralized administrator authentication
* Role-based authorization
* Command authorization
* Accounting
* Audit logging

---

## 16. Guest Access Architecture

```text
Guest User
    |
    v
Guest Portal
    |
    v
Cisco ISE
    |
    v
Guest Authorization
    |
    v
Internet-Only Access
```

Guest access should be isolated from internal enterprise resources.

---

## 17. ISE High Availability

The architecture should provide:

* Multiple PSNs
* Redundant authentication services
* PAN redundancy
* MnT redundancy where required
* Multiple RADIUS servers configured on network devices
* Geographic distribution where appropriate

### Failure Scenarios

| Failure              | Expected Behavior                                             |
| -------------------- | ------------------------------------------------------------- |
| PSN failure          | Authentication uses alternate PSN                             |
| PAN failure          | Policy administration remains available through secondary PAN |
| Directory failure    | Defined authentication fallback applies                       |
| Network path failure | Alternate path is used                                        |
| MnT failure          | Authentication continues; monitoring is impacted              |

---

## 18. Security Controls

ISE architecture supports:

* 802.1X
* MAB
* RADIUS
* TACACS+
* Endpoint profiling
* Dynamic authorization
* SGT assignment
* Guest access control
* Posture assessment
* Security logging

---

## 19. Monitoring and Logging

ISE monitoring should include:

* Authentication success and failure
* MAB events
* Authorization results
* Endpoint profiling
* Policy violations
* Administrative activity
* System health

ISE events should integrate with:

* SIEM
* Monitoring platforms
* ITSM platforms

---

## 20. ISE Integration Matrix

| System                | Integration          | Purpose               |
| --------------------- | -------------------- | --------------------- |
| Network Devices       | RADIUS               | Authentication        |
| Network Devices       | TACACS+              | Administration        |
| Active Directory      | LDAP / Kerberos      | Identity              |
| Catalyst Center       | API                  | SDA integration       |
| SIEM                  | Syslog / API         | Security monitoring   |
| ServiceNow            | API                  | Incident and workflow |
| Certificate Authority | Certificate Services | EAP-TLS               |

---

## 21. Security and Operational Requirements

The ISE architecture must provide:

* Secure authentication
* High availability
* Centralized policy management
* Auditability
* Role-based administration
* Secure integration
* Backup and recovery
* Monitoring and alerting

---

## 22. Architecture Summary

Cisco ISE provides the identity and policy foundation for the Enterprise Network Transformation.

It enables the transition from traditional location-based network access toward an identity-based security model.

The architecture integrates authentication, authorization, profiling, segmentation, administrative access control, and security monitoring with the wider enterprise network architecture.

ISE is a critical component of the target architecture and provides the policy foundation for Cisco SD-Access and identity-based network security.


