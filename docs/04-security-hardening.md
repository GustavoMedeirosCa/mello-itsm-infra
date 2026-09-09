# 04 — Security Hardening Checklist

Running log of security decisions made during Phase 1, and what's still
open. Update this file as further hardening happens.

## Done

- [x] `PermitRootLogin yes` set deliberately (internal network only) —
      documented trade-off, see `02-base-os-and-network.md`
- [x] GLPI default accounts (`glpi`, `tech`, `normal`, `post-only`)
      rotated off their factory passwords
- [x] GLPI demo data disabled
- [x] `install/install.php` removed after install completed
- [x] `config/`, `files/`, `log/` relocated outside the web-served
      directory (`/etc/glpi`, `/var/lib/glpi/files`, `/var/log/glpi`)
- [x] MariaDB `glpi` user scoped to `localhost` only, own database only

## Hardening approach

Every default credential and demo setting introduced during install is
treated as temporary and rotated out as a standard step, not an
afterthought (see "Done" above for what's already been applied).

Specific outstanding hardening items for this live, named production
system are tracked in a private checklist, not published here — a
public "known gaps" list for a real, identifiable server is itself
useful information to an attacker, regardless of portfolio value.

## Credentials handling

**Actual credentials are never stored in this repository.** They live in
a password manager; see `.gitignore` for the pattern excluding any local
`credenciais-*.md` / `credentials-*.md` reference files from being
committed by accident.