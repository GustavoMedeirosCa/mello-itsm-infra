# Mello Transportes — ITSM & Monitoring Infrastructure

Infrastructure-as-documentation repository for Mello Transportes' internal
IT Service Management and Monitoring stack, built on Debian 12 (Bookworm).

This repo tracks the design decisions, configuration, and step-by-step
build log for the project — not the deployed application code itself
(GLPI, Zabbix, etc. are third-party software installed on the server).

## Project Phases

### Phase 1 — ITSM Core (in progress)
- [x] Base OS install & hardening (Debian 12)
- [x] Static network configuration
- [x] LAMP stack (Apache, MariaDB, PHP 8.2)
- [x] GLPI 11 installation & secure directory layout
- [x] Default credentials rotated, demo data disabled
- [x] Automatic actions verified running in CLI mode via cron
- [ ] Active Directory / LDAP integration
- [ ] Group Policy (GPO) rollout of GLPI Agent
- [ ] Self-Service portal UX configuration
- [ ] Scheduled/portable inventory via cron

### Phase 2 — Monitoring & Communications (planned)
- [ ] Zabbix server + Grafana dashboards
- [ ] Mail gateway
- [ ] Telegram bot integration (GLPI ticket alerts + Zabbix network alerts, zero recurring cost)

## Infrastructure Overview

| Component | Value |
|---|---|
| Hypervisor | VMware ESXi 7.0 U2 (`192.0.2.10`) |
| VM name | `SRV--GLPI` |
| OS | Debian 12 "Bookworm" |
| Web stack | Apache 2.4 + MariaDB + PHP 8.2 |
| ITSM application | GLPI 11 |
| Current IP (temporary) | `192.0.2.229` |
| Production IP (planned) | `192.0.2.228` |

See [`docs/`](./docs) for the detailed build log and rationale behind each
configuration decision.

## Repository Structure

itsm-infra/
├── README.md
└── docs/
├── 01-infrastructure-overview.md
├── 02-base-os-and-network.md
├── 03-lamp-and-glpi-installation.md
└── 04-security-hardening.md

## Conventions

- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org/)
  (`feat:`, `fix:`, `docs:`, `chore:`, ...).
- Documentation is written in English; the deployed applications
  (GLPI, etc.) remain in Portuguese for end users at Mello Transportes.
- Credentials are **never** committed to this repository. See
  `.gitignore` and keep secrets in a password manager instead.

## Author

Maintained by TI — Mello Transportes (`ti@mellotransportes.com.br`).