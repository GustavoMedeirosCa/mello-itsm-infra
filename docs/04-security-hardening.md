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

## Open / planned

- [ ] Migrate SSH from password auth to key-based auth, then restore
      `PermitRootLogin prohibit-password`
- [ ] Rotate the MariaDB `glpi` user's password (it appeared in plaintext
      during setup chat/logs — low risk since it's `localhost`-only, but
      good practice to rotate)
- [ ] Move to HTTPS (self-signed or internal CA cert) once the server is
      reachable at its final production IP/hostname
- [ ] Configure LDAP/Active Directory authentication for real users,
      reducing reliance on local GLPI accounts

## Credentials handling

**Actual credentials are never stored in this repository.** They live in
a password manager; see `.gitignore` for the pattern excluding any local
`credenciais-*.md` / `credentials-*.md` reference files from being
committed by accident.