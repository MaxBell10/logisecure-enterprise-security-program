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

## Global Architecture

```
LOGISECURE SA — INFRASTRUCTURE

INTERNET/WAN
    │
[pfSense CE — Firewall/Router]              → logisecure-pfsense-segmentation
    │
    ├── [LAN IT — 192.168.1.x]
    │       Active Directory (lab.local)    → logisecure-active-directory
    │       Wazuh SIEM                      → logisecure-active-directory
    │       PKI / KMS                       → logisecure-pki-kms
    │
    ├── [DMZ — 192.168.2.x]
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

---

## Programme Overview

| Part | Name | Repositories |
|---|---|---|
| Hub | Enterprise Security Program | logisecure-enterprise-security-program |
| 1 | Build the Lab | active-directory → attack-simulation |
| 2 | Expand the Skills | ot-network-security → redteam-blueteam |
| 3 | Govern the Risk | legacy-ot-security → iso27001-audit |

### Part 1 — Build the Lab

| Repository | Status | Description |
|---|---|---|
| [logisecure-active-directory](https://github.com/MaxBell10/logisecure-active-directory) | 🔄 In progress | AD hardening · GPO · Wazuh SIEM · MITRE ATT&CK |
| [logisecure-pfsense-segmentation](https://github.com/MaxBell10/logisecure-pfsense-segmentation) | 🔄 In progress | pfSense · Suricata IDS/IPS · DMZ · OpenVAS |
| [logisecure-ebios-rm-assessment](https://github.com/MaxBell10/logisecure-ebios-rm-assessment) | 📋 Planned | EBIOS RM 5 workshops · NIS2 · strategic scenarios |
| [logisecure-bash-automation](https://github.com/MaxBell10/logisecure-bash-automation) | 📋 Planned | Bash & PowerShell · GPG-signed · GitHub Actions CI |
| [logisecure-attack-simulation](https://github.com/MaxBell10/logisecure-attack-simulation) | 📋 Planned | Kill chain · password spray · Wazuh correlation |

### Part 2 — Expand the Skills

| Repository | Status | Description |
|---|---|---|
| [logisecure-ot-network-security](https://github.com/MaxBell10/logisecure-ot-network-security) | 📋 Planned | Purdue Model · VLAN · ACL · IEC 62443 |
| [logisecure-pki-kms](https://github.com/MaxBell10/logisecure-pki-kms) | 📋 Planned | 2-tier PKI · Root CA offline · CRL · GPG |
| [logisecure-honeypot-threat-intel](https://github.com/MaxBell10/logisecure-honeypot-threat-intel) | 📋 Planned | Cowrie · STIX IOC export · Threat Intel |
| [logisecure-container-security](https://github.com/MaxBell10/logisecure-container-security) | 📋 Planned | Docker hardening · Trivy · kube-bench · SBOM |
| [logisecure-cloud-security](https://github.com/MaxBell10/logisecure-cloud-security) | 📋 Planned | AWS · Terraform IaC · GuardDuty · CloudTrail |
| [logisecure-forensics-ir](https://github.com/MaxBell10/logisecure-forensics-ir) | 📋 Planned | PICERL · TheHive · memory & disk forensics |
| [logisecure-redteam-blueteam](https://github.com/MaxBell10/logisecure-redteam-blueteam) | 📋 Planned | Purple Team · MTTD · 13 MITRE techniques |

### Part 3 — Govern the Risk

| Repository | Status | Description |
|---|---|---|
| [logisecure-legacy-ot-security](https://github.com/MaxBell10/logisecure-legacy-ot-security) | 📋 Planned | Legacy HMI · virtual patching · risk treatment |
| [logisecure-supply-chain-risk](https://github.com/MaxBell10/logisecure-supply-chain-risk) | 📋 Planned | Vendor assessment · SBOM Syft/Grype · MFA VPN |
| [logisecure-iso27001-audit](https://github.com/MaxBell10/logisecure-iso27001-audit) | 📋 Planned | SoA · Annex A audit · NC report · action plan |

---

## CISO Dashboard — Consolidated KPIs

> **Reading guide:** `Target` = objective defined in the programme · `Actual` = measured value after project completion

| KPI | Target | Actual | Repository |
|---|---|---|---|
| Purple Team MTTD | < 120s | `TBD` | logisecure-redteam-blueteam |
| MITRE techniques detected | ≥ 11 / 13 tested | `TBD` | logisecure-redteam-blueteam |
| Critical Docker CVEs reduction | > 90% | `TBD` | logisecure-container-security |
| Custom Wazuh rules | ≥ 15 | `TBD` | multiple |
| Network segments | 5 | `TBD` | logisecure-pfsense-segmentation |
| Legacy OT risk level | CRITICAL → MEDIUM | `TBD` | logisecure-legacy-ot-security |
| ISO 27001 Annex A controls audited | ≥ 20 | `TBD` | logisecure-iso27001-audit |
| Major NCs identified | documented | `TBD` | logisecure-iso27001-audit |
| Suppliers assessed | 3 | `TBD` | logisecure-supply-chain-risk |
| PingCastle AD score improvement | significant reduction | `TBD` | logisecure-active-directory |
| OpenVAS critical vulns (DC) | 0 after remediation | `TBD` | logisecure-pfsense-segmentation |

---

## Security Posture — Executive Summary

| Domain | Maturity | Repository |
|---|---|---|
| Identity & Access Management | `TBD` | logisecure-active-directory |
| Network Segmentation | `TBD` | logisecure-pfsense-segmentation |
| Cryptography & PKI | `TBD` | logisecure-pki-kms |
| Threat Detection | `TBD` | logisecure-active-directory · logisecure-honeypot-threat-intel |
| Cloud Security | `TBD` | logisecure-cloud-security |
| OT / ICS Security | `TBD` | logisecure-ot-network-security · logisecure-legacy-ot-security |
| Incident Response | `TBD` | logisecure-forensics-ir |
| Supplier Risk | `TBD` | logisecure-supply-chain-risk |
| GRC & Compliance | `TBD` | logisecure-ebios-rm-assessment · logisecure-iso27001-audit |
| Security Awareness | Gap identified | logisecure-iso27001-audit — A.6.3 NC |

---

## Risk Register

| Risk | Impact | Likelihood | Mitigation | Repository |
|---|---|---|---|---|
| AD compromise — password spray | CRITICAL | MEDIUM | Account lockout · Wazuh rule · MFA | logisecure-active-directory |
| Lateral movement IT → OT | CRITICAL | MEDIUM | VLAN · pfSense ACL · Suricata IPS | logisecure-pfsense-segmentation |
| Ransomware via phishing (WMS) | CRITICAL | HIGH | Email filtering · backup · IR playbook | logisecure-ebios-rm-assessment |
| Unsecured third-party VPN (OT) | HIGH | HIGH | MFA VPN · ACL · session timeout · logs | logisecure-supply-chain-risk |
| API partner data leak | HIGH | MEDIUM | TLS · vendor assessment · SBOM | logisecure-supply-chain-risk |
| Legacy OT unpatched exploit | HIGH | MEDIUM | Virtual patching · VLAN · Zeek | logisecure-legacy-ot-security |
| S3 cloud exfiltration | HIGH | LOW | Public access block · GuardDuty | logisecure-cloud-security |
| Software supply chain compromise | HIGH | LOW | SBOM Syft/Grype · image scanning | logisecure-container-security |

---

## Regulatory & Framework Coverage

| Framework | Coverage |
|---|---|
| **ISO 27001:2022** | Annex A — A.5 Policies · A.6 People · A.7 Physical · A.8 Technological |
| **NIS2 Art. 21** | Risk management · Supply chain · Access control · Incident handling · Continuity |
| **IEC 62443** | SL1–SL2 · SR 1.1–1.3 · SR 5.1–5.4 · Purdue Model · IT/OT segmentation |
| **EBIOS RM** | 5 workshops · Strategic & operational scenarios · Residual risk treatment |
| **MITRE ATT&CK Enterprise** | T1078 · T1110 · T1484 · T1566 · T1195 · T1562 · T1021 · T1133 |
| **MITRE ATT&CK for ICS** | T0862 · T0859 · T0814 · T0813 · T0849 · T0822 |
| **CIS Controls** | Control 5 — Account Mgmt · Control 8 — Audit Logs · Control 12 — Network Infra |

---

## Flagship Projects

| Repository | Why flagship | Key metric |
|---|---|---|
| [logisecure-redteam-blueteam](https://github.com/MaxBell10/logisecure-redteam-blueteam) | Purple Team — full system vision | MTTD · 11/13 techniques detected |
| [logisecure-iso27001-audit](https://github.com/MaxBell10/logisecure-iso27001-audit) | SoA + audit report — rare GRC profile | 2 major NCs documented |
| [logisecure-attack-simulation](https://github.com/MaxBell10/logisecure-attack-simulation) | AD + pfSense + detection + incident report | Complete kill chain |
| [logisecure-active-directory](https://github.com/MaxBell10/logisecure-active-directory) | IAM + SIEM foundation — base of everything | PingCastle score before/after |
| [logisecure-cloud-security](https://github.com/MaxBell10/logisecure-cloud-security) | Terraform IaC + AWS — highly in demand | GuardDuty + compliance |

---

## Certification Coverage

| Repository | Security+ | CCNA | SecOT+ | CISSP |
|---|---|---|---|---|
| logisecure-active-directory | IAM, SIEM | — | — | D5 |
| logisecure-pfsense-segmentation | Network | ACL, VLAN | — | D4 |
| logisecure-ebios-rm-assessment | Risk | — | Risk OT | D1 |
| logisecure-bash-automation | Automation | — | — | D7 |
| logisecure-attack-simulation | Threats | Routing | — | D7 |
| logisecure-ot-network-security | ICS/SCADA | VLANs | OT Net | D7 |
| logisecure-pki-kms | Crypto | — | — | D3 |
| logisecure-honeypot-threat-intel | Threat Intel | — | — | D7 |
| logisecure-container-security | Virtualisation | — | — | D7 |
| logisecure-cloud-security | Cloud Sec | — | — | D3/D7 |
| logisecure-forensics-ir | IR | — | — | D7 |
| logisecure-redteam-blueteam | Pentest | CCNA | OT threats | D7 |
| logisecure-legacy-ot-security | ICS | — | Legacy | D7 |
| logisecure-supply-chain-risk | Supply | — | OT vendors | D1 |
| logisecure-iso27001-audit | Risk Mgmt | — | — | D1 |

---

<div align="center">

*All environments simulate the fictional enterprise LogiSecure SA, used solely for educational and portfolio purposes.*

*Built by [Maxime Belliard](https://github.com/MaxBell10) — Cybersecurity Analyst · Technical & GRC · End-to-End Implementation*

</div>
