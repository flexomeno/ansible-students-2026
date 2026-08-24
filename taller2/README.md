# Taller 2 — Roles: instalar Apache y actualizar CSS (entrega del alumno)

Objetivo
- Entregar una implementación basada en roles que instale Apache, despliegue una plantilla HTML y un archivo CSS, y que utilice un `ansible.cfg` de proyecto.

Estructura esperada (archivos que debes crear)
- `taller2/ansible.cfg` — configuración del proyecto (inventory por defecto, roles_path, retry_files_enabled).
- `taller2/host.ini` — inventario INI.
- `taller2/install_server.yml` — playbook principal que invoca el/los roles.
- `taller2/webserver/` — rol con estructura estándar (`tasks/main.yml`, `templates/index.html.j2`, `templates/style.css.j2`, `vars/main.yml`, `handlers/main.yml`).
- (Opcional) `taller2/update_css/` — role o tareas separadas para actualizar estilos.
- `taller2/README.md` — este archivo.

Pasos mínimos
1. Crear rama: `git checkout -b taller-2/<tu_usuario>`
2. Implementar `ansible.cfg`, inventario y roles en `taller2/`.
3. Verificaciones:
   - `ansible-playbook --syntax-check -i taller2/host.ini taller2/install_server.yml`
   - `ansible-lint taller2/webserver/` (o `ansible-lint .`)
   - `ansible-playbook -i taller2/host.ini taller2/install_server.yml --check --diff`
4. Ejecutar real y comprobar:
   - `ansible-playbook -i taller2/host.ini taller2/install_server.yml`
   - `curl -sS http://<host>/ | head -n 20`
   - `curl -sS http://<host>/style.css | head -n 50` para comprobar que el CSS fue desplegado.
5. Idempotencia: segunda ejecución sin cambios.

Requisitos técnicos mínimos del rol `webserver`
- Instalar Apache (`apache2` o `httpd`) según la familia OS.
- Usar `template` para `index.html` y `style.css` con variables (`background_color`, `title_color`, etc.).
- Manejar reinicio del servicio con handlers cuando cambie la plantilla.

Ejemplo mínimo de `ansible.cfg` que pedimos
```
[defaults]
inventory = host.ini
roles_path = ./roles:./
retry_files_enabled = False
deprication_warnings = False
```

Entregable
- Estructura del rol, `ansible.cfg`, inventario, playbook y README con evidencia.

Evaluación (sugerida)
- Uso correcto de roles y handlers (40%), despliegue correcto del CSS y plantilla (30%), lint y sintaxis (10%), idempotencia y documentación (20%).
