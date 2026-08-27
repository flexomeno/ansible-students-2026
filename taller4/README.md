# Taller 4 — Despliegue de aplicación y systemd (entrega del alumno)

Objetivo
- Desplegar una aplicación simple (script, binario o sitio) y crear/gestionar una unidad systemd para ejecutarla como servicio.

Archivos esperados
- `taller4/host.ini`
- `taller4/deploy_app.yml` (playbook)
- `taller4/templates/` (unit file systemd jinja2, configuración de la app)
- `taller4/README.md` — este archivo.

Requisitos funcionales mínimos
- Copiar artefacto o código al directorio objetivo (ej. `/opt/myapp`).
- Crear un unit file systemd en `/etc/systemd/system/` usando `template`.
- Recargar systemd y habilitar/iniciar el servicio.
- Verificar logs: `journalctl -u <servicio> -n 100`.

Validaciones que debes incluir
- `systemctl status <servicio>` (activo y habilitado)
- `ss -tlnp | grep <puerto>` o `curl` si el servicio expone HTTP
- `journalctl -u <servicio> -n 50` (salidas relevantes)

Entregable
- Playbook, templates, inventario y README con evidencia.
