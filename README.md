# LogiSecure Enterprise Security Program

[![Hub](https://img.shields.io/badge/LogiSecure-Enterprise%20Security%20Program-1F3864?style=flat-square)](https://github.com/MaxBell10/logisecure-enterprise-security-program)
[![ISO 27001](https://img.shields.io/badge/ISO%2027001-2022-EF7730?style=flat-square)](https://www.iso.org)
[![IEC 62443](https://img.shields.io/badge/IEC%2062443-OT%20Security-8B5CF6?style=flat-square)](https://www.iec.ch)
[![NIS2](https://img.shields.io/badge/NIS2-Compliant%20Programme-3B8ADB?style=flat-square)](https://digital-strategy.ec.europa.eu)
[![EBIOS RM](https://img.shields.io/badge/EBIOS%20RM-Risk%20Assessment-F59E0B?style=flat-square)](https://www.ssi.gouv.fr)
[![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK%20Mapped-E05252?style=flat-square)](https://attack.mitre.org)

> **This is the central hub of a 16-project cybersecurity portfolio simulating a full enterprise security programme for LogiSecure SA — a fictional Belgian logistics operator.**
> The programme covers identity management, network segmentation, OT security, cloud, GRC, and incident response — built end-to-end as a CISO-level portfolio.

---

## LogiSecure SA — Fictional Enterprise Context

| Attribute | Detail |
|---|---|
| **Sector** | Automated logistics operator — conveyors, WMS, B2B e-commerce |
| **Size** | 500 employees · HQ Brussels, Belgium |
| **Regulatory scope** | NIS2 (Jan 2025) · ISO 27001 · IEC 62443 (OT) |
| **IT infrastructure** | Active Directory `lab.local` · pfSense · Wazuh SIEM · AWS `eu-west-1` |
| **OT infrastructure** | Legacy conveyor HMI (Windows 7) · PLC · WMS · Historian SCADA |
| **Suppliers** | TechLogix BVBA (WMS) · ConveyorPro GmbH (OT) · DataAPI SAS (API) |
| **Key risks** | Ransomware · IT→OT lateral movement · API data leak · Supply chain compromise |

---

## ⭐ Flagship Projects — Start Here

> Start with the completed repositories — each one demonstrates a measurable, evidenced security outcome. The planned flagships follow with their target outcome, and will be linked once published.

| Repository | What it demonstrates | Key metric |
|---|---|---|
| [logisecure-active-directory](https://github.com/MaxBell10/logisecure-active-directory) | IAM + SIEM foundation — base of everything | PingCastle 55/100 · Privileged Accounts -10pts · 3 MITRE rules |
| [logisecure-pfsense-segmentation](https://github.com/MaxBell10/logisecure-pfsense-segmentation) | Network segmentation + detection wired into the SIEM | 12 rules, default-deny · DMZ→LAN scans alerted in Wazuh (T1046) · vulnerability scanner validated against nmap |

**Planned flagships**

| Repository | What it will demonstrate | Target outcome |
|---|---|---|
| logisecure-redteam-blueteam | Purple Team — full system vision | MTTD < 120s · ≥ 11/13 MITRE techniques detected |
| logisecure-attack-simulation | AD + pfSense + detection + incident report | Complete kill chain documented |
| logisecure-iso27001-audit | SoA + audit report — rare GRC profile | ≥ 20 Annex A controls audited · NCs documented |
| logisecure-cloud-security | Terraform IaC + AWS — highly in demand | GuardDuty + compliance |

---

## Global Architecture

```
LOGISECURE SA — INFRASTRUCTURE

INTERNET/WAN
    │
[pfSense CE — Firewall/Router]              → logisecure-pfsense-segmentation
    │
    ├── [LAN IT — 10.10.10.x]
    │       Active Directory (lab.local)    → logisecure-active-directory
    │       DC01: 10.10.10.10               → logisecure-active-directory
    │       WKS01: 10.10.10.20              → logisecure-active-directory
    │       Wazuh SIEM: 10.10.10.30         → logisecure-active-directory
    │       PKI / KMS                       → logisecure-pki-kms
    │
    ├── [DMZ — 10.10.20.x]
    │       Cowrie Honeypot                 → logisecure-honeypot-threat-intel
    │       Web server (supplier-facing)    → logisecure-honeypot-threat-intel
    │
    ├── [OT Control VLAN 20]
    │       HMI legacy (Windows 7)          → logisecure-legacy-ot-security
    │       Historian SCADA                 → logisecure-ot-network-security
    │
    └── [OT Field VLAN 30]
            PLC · Sensors · Conveyors       → logisecure-ot-network-security

[AWS Cloud — eu-west-1]                     → logisecure-cloud-security
    IAM · S3 · CloudTrail · GuardDuty · Terraform

[Third-party VPN]                           → logisecure-supply-chain-risk
    TechLogix · ConveyorPro · DataAPI
```

> **Architecture note:** The current design follows a perimeter-based model (pfSense zones, Purdue Model for OT). The planned evolution towards Zero Trust — micro-segmentation, continuous AD identity validation, and conditional access — is documented in the improvement roadmap of [logisecure-pfsense-segmentation](https://github.com/MaxBell10/logisecure-pfsense-segmentation).

---

## Programme Overview

| Part | Name | Repositories |
|---|---|---|
| Hub | Enterprise Security Program | logisecure-enterprise-security-program |
| 1 | Build the Lab | active-directory → attack-simulation |
| 2 | Expand the Skills | ot-network-security → redteam-blueteam |
| 3 | Govern the Risk | legacy-ot-security → iso27001-audit |

> Planned projects are listed by name and linked once their repository is published.

### Part 1 — Build the Lab

| Repository | Status | Description |
|---|---|---|
| [logisecure-active-directory](https://github.com/MaxBell10/logisecure-active-directory) | ✅ Completed | AD hardening · 4 GPOs · Wazuh SIEM · 3 MITRE ATT&CK rules · PingCastle 55/100 |
| [logisecure-pfsense-segmentation](https://github.com/MaxBell10/logisecure-pfsense-segmentation) | ✅ Completed | LAN · DMZ segmentation · 12 rules, default-deny · Suricata IDS/IPS ×3 · alerts in Wazuh · MITRE T1046 · OpenVAS validated against nmap |
| logisecure-ebios-rm-assessment | 📋 Planned | EBIOS RM 5 workshops · NIS2 · strategic scenarios |
| logisecure-bash-automation | 📋 Planned | Bash & PowerShell · GPG-signed · GitHub Actions CI |
| logisecure-attack-simulation | 📋 Planned | Kill chain · password spray · Wazuh correlation |

### Part 2 — Expand the Skills

| Repository | Status | Description |
|---|---|---|
| logisecure-ot-network-security | 📋 Planned | Purdue Model · VLAN · ACL · IEC 62443 |
| logisecure-pki-kms | 📋 Planned | 2-tier PKI · Root CA offline · CRL · GPG |
| logisecure-honeypot-threat-intel | 📋 Planned | Cowrie · STIX IOC export · Threat Intel |
| logisecure-container-security | 📋 Planned | Docker hardening · Trivy · kube-bench · SBOM |
| logisecure-cloud-security | 📋 Planned | AWS · Terraform IaC · GuardDuty · CloudTrail |
| logisecure-forensics-ir | 📋 Planned | PICERL · TheHive · memory & disk forensics |
| logisecure-redteam-blueteam | 📋 Planned | Purple Team · MTTD · 13 MITRE techniques |

### Part 3 — Govern the Risk

| Repository | Status | Description |
|---|---|---|
| logisecure-legacy-ot-security | 📋 Planned | Legacy HMI · virtual patching · risk treatment |
| logisecure-supply-chain-risk | 📋 Planned | Vendor assessment · SBOM Syft/Grype · MFA VPN |
| logisecure-iso27001-audit | 📋 Planned | SoA · Annex A audit · NC report · action plan |

---

## CISO Dashboard — Consolidated KPIs

> **Reading guide:** `Target` = objective defined in the programme · `Actual` = measured value after project completion

| KPI | Target | Actual | Repository |
|---|---|---|---|
| Purple Team MTTD | < 120s | `TBD` | logisecure-redteam-blueteam |
| MITRE techniques detected | ≥ 11 / 13 tested | `TBD` | logisecure-redteam-blueteam |
| Critical Docker CVEs reduction | > 90% | `TBD` | logisecure-container-security |
| Custom Wazuh rules | ≥ 15 | **3 / 15** ✅ (T1110, T1078, T1087) | logisecure-active-directory |
| Network segments | 5 | **2 / 5** — LAN · DMZ | logisecure-pfsense-segmentation · logisecure-ot-network-security · logisecure-cloud-security |
| Legacy OT risk level | CRITICAL → MEDIUM | `TBD` | logisecure-legacy-ot-security |
| ISO 27001 Annex A controls audited | ≥ 20 | `TBD` | logisecure-iso27001-audit |
| Major NCs identified | documented | `TBD` | logisecure-iso27001-audit |
| Suppliers assessed | 3 | `TBD` | logisecure-supply-chain-risk |
| PingCastle AD score | significant reduction | **55/100** · Privileged Accounts -10pts · Stale Objects -5pts | logisecure-active-directory |
| OpenVAS critical vulns (DC) | 0 after remediation | 0 Critical · 0 High (unauthenticated scan) — authenticated scan + remediation carried over ⚠️ | logisecure-pfsense-segmentation |

---

## Security Posture — Executive Summary

| Domain | Maturity | Repository |
|---|---|---|
| Identity & Access Management | **Established** — AD hardened · 4 GPOs · 6 users · MachineAccountQuota=0 · Recycle Bin · AES256 | logisecure-active-directory |
| Network Segmentation | **Established** — LAN · DMZ behind pfSense · 12 justified rules, default-deny · DMZ→LAN blocked and logged · LAN still flat (no micro-segmentation) | logisecure-pfsense-segmentation |
| Cryptography & PKI | `TBD` | logisecure-pki-kms |
| Threat Detection | **Initial** — Wazuh v4.14.5 · 2 agents + Suricata DMZ sensor (syslog) · 3 MITRE rules (AD) + T1046 (network scans) · baseline alerting | logisecure-active-directory · logisecure-pfsense-segmentation · logisecure-honeypot-threat-intel |
| Cloud Security | `TBD` | logisecure-cloud-security |
| OT / ICS Security | `TBD` | logisecure-ot-network-security · logisecure-legacy-ot-security |
| Incident Response | `TBD` | logisecure-forensics-ir |
| Supplier Risk | `TBD` | logisecure-supply-chain-risk |
| GRC & Compliance | `TBD` | logisecure-ebios-rm-assessment · logisecure-iso27001-audit |
| Security Awareness | Gap identified | logisecure-iso27001-audit — A.6.3 NC |

---

## Risk Register — Top Risks

| Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|
| AD compromise — password spray | CRITICAL | MEDIUM | Account lockout · Wazuh rule T1110 · MFA |
| Lateral movement IT → OT | CRITICAL | MEDIUM | VLAN · pfSense ACL · Suricata IPS |
| Ransomware via phishing (WMS) | CRITICAL | HIGH | Email filtering · backup · IR playbook |
| Unsecured third-party VPN (OT) | HIGH | HIGH | MFA VPN · ACL · session timeout · logs |

> Full risk register (8 risks · EBIOS RM mapped) → [`docs/risk-register.md`](docs/risk-register.md)

---

## Regulatory & Framework Coverage

The programme covers **ISO 27001:2022** (Annex A), **NIS2 Art. 21**, **IEC 62443** (SL1–SL2, Purdue Model), **EBIOS RM** (5 workshops), **MITRE ATT&CK** Enterprise + ICS, and **CIS Controls** (5, 8, 12).

> Full framework mapping → [`docs/framework-coverage.md`](docs/framework-coverage.md)

---

## Certification Coverage

Each repository contributes to at least one certification domain: **Security+**, **CCNA**, **CISSP** (D1–D7). Flagship projects cover the broadest range across all four.

> Full certification mapping per repository → [`docs/certification-coverage.md`](docs/certification-coverage.md)

---

<div align="center">

*All environments simulate the fictional enterprise LogiSecure SA, used solely for educational and portfolio purposes.*

*Built by [Maxime Belliard](https://github.com/MaxBell10) — Cybersecurity Analyst · Technical & GRC · End-to-End Implementation*

</div>
