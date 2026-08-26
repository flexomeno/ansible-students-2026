# Taller 3 — Gestión de usuarios y sudoers (entrega del alumno)

Objetivo
- Crear playbook/role que gestione usuarios, sus claves SSH, grupos y configuraciones sudo en los hosts objetivo.

Archivos esperados
- `taller3/host.ini`
- `taller3/manage_users.yml` (o rol `users/` con tasks/vars/templates)
- `taller3/README.md` — este archivo.

Requisitos funcionales mínimos
- Crear usuarios indicados en una lista de variables.
- Añadir usuarios a grupos (ej. `sudo`, `wheel`) según el SO.
- Copiar claves públicas SSH a `~/.ssh/authorized_keys`.
- Crear archivos en `/etc/sudoers.d/` si es necesario (usar `copy` con `mode: '0440'`).
- Manejar idempotencia (ejecutar dos veces no debe re-crear ni romper permisos).

Validaciones que debes incluir en tu README
- `getent passwd <user>`
- `id <user>`
- Chequeo de `authorized_keys` y permisos: `ls -la /home/<user>/.ssh`
- Presencia y permisos correctos en `/etc/sudoers.d/`

Entregable
- Playbook/role, inventario y README con evidencia (comandos y salidas).
