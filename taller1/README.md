# Taller 1 — Instalar Apache (entrega del alumno)

Objetivo
- Crear un inventario `host.ini` y un playbook `install_apache.yml` que instale y habilite Apache en el host objetivo y despliegue una página `index.html` simple.

Archivos que debes crear
- `taller1/host.ini` — inventario INI con el/los hosts de prueba.
- `taller1/install_apache.yml` — playbook que realice la instalación, copia del index y asegure el servicio.
- `taller1/README.md` — este archivo (completa con evidencia en tu rama de entrega).

Pasos mínimos que debes seguir
1. Clonar el repo y crear rama: `git checkout -b taller-1/<tu_usuario>`
2. Crear/activar venv e instalar dependencias: `python -m venv .venv && source .venv/bin/activate && pip install --upgrade pip && pip install ansible ansible-lint`
3. Implementar `host.ini` y `install_apache.yml` en `taller1/`.
4. Ejecutar comprobaciones:
   - `ansible-playbook --syntax-check -i taller1/host.ini taller1/install_apache.yml`
   - `ansible-lint taller1/install_apache.yml`
   - `ansible-playbook -i taller1/host.ini taller1/install_apache.yml --check --diff`
5. Ejecutar el playbook real:
   - `ansible-playbook -i taller1/host.ini taller1/install_apache.yml`
6. Validar en el host:
   - `systemctl status apache2 || systemctl status httpd`
   - `curl -sS http://<host> | head -n 20`
   - Verificar puerto 80 escuchando: `ss -tlnp | grep :80`
7. Idempotencia: volver a ejecutar el playbook y confirmar 0 cambios en la segunda pasada.

Entregable (en la rama del alumno)
- `taller1/host.ini`
- `taller1/install_apache.yml`
- `taller1/README.md` completo con evidencia (salidas de comandos, capturas, notas de problemas).

Evaluación (sugerida)
- Correctitud funcional (50%), calidad del playbook y uso de become/handlers (20%), lint y sintaxis (10%), documentación y evidencia (10%), idempotencia y buenas prácticas (10%).
