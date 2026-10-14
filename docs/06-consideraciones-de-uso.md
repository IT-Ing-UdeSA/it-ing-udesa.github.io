# Consideraciones de uso

Cosas a tener en cuenta para usar las máquinas del laboratorio, que son compartidas entre materias y usuarios.
## Buenas prácticas
- No compartir credenciales con otras personas de la universidad.
- Una vez que terminen de usar la máquina, cerrar la sesión para que no queden procesos abiertos y para que no sea posible leer la información sensible de un usuario.
- Si se alejan de una máquina del laboratorio sin cerrar la sesión, bloquear la pantalla (`Super+L`).
- Consultar el calendario de la [portada](index.md) para ver la disponibilidad del laboratorio.
- Antes del final del cuatrimestre, mover al home lo que se quiera conservar de `~/scratch`.

## Instalación de software local

Es posible instalar software local dentro del $HOME o incluso dentro del disco local de la máquina. Está bajo su responsabilidad instalar software seguro y mantenerlo actualizado.

Los usuarios no tienen permisos de administrador, por lo que no pueden usar `apt`. Algunas alternativas:
- Paquetes de Python: dentro de un entorno virtual (ver la sección "Entornos de Python y software propio", más abajo).
- Herramientas de línea de comandos publicadas en PyPI: `uv tool install <herramienta>`.
- Binarios precompilados o programas compilados desde el código fuente: instalarlos en `~/scratch`.

Para pedir que un programa se instale globalmente en el sistema, ver [Solicitud e instalación de software](07-acuerdo-de-nivel-de-servicio.md#7-solicitud-e-instalación-de-software).

## Recursos compartidos

Las máquinas del laboratorio son compartidas entre múltiples estudiantes de la universidad. Es recomendable chequear con programas como _btop_ o _nvtop_ cuál es el porcentaje de uso de los recursos antes de lanzar un trabajo.

## Varias terminales en una conexión (tmux)

Como hay un [límite de conexiones simultáneas](02-acceso.md#acceso-remoto-por-ssh), para trabajar con varias terminales a la vez se recomienda usar [tmux](https://github.com/tmux/tmux/wiki/Getting-Started), que permite abrir múltiples ventanas y dividir la pantalla en paneles dentro de una misma conexión.

Si la conexión SSH o la VPN se corta, incluido el corte diario de las 07:00, la sesión de tmux sigue corriendo en la máquina y se puede retomar con `tmux attach`. tmux no sobrevive al reinicio diario de las máquinas de las 07:30 (ver [Disponibilidad y mantenimiento](07-acuerdo-de-nivel-de-servicio.md#6-disponibilidad-y-mantenimiento)).

## Entornos de Python y software propio

Para entornos de Python, se recomienda utilizar _uv_ (https://docs.astral.sh/uv/) para crear virtual environments de Python. Las cachés de uv ya están configuradas para guardarse en `~/scratch`.

Un entorno virtual puede ocupar varios GB, por lo que debe crearse en `~/scratch` y no en el home:

```
uv venv ~/scratch/work/venvs/<proyecto>
source ~/scratch/work/venvs/<proyecto>/bin/activate
uv pip install -r requirements.txt
```

Si se usan proyectos de uv (`uv init`, `uv sync`) con el código en el home, uv crea el entorno en la carpeta `.venv` del proyecto, es decir, dentro del home. Para evitarlo, definir `UV_PROJECT_ENVIRONMENT` con una ruta en `~/scratch`.

Como `~/scratch` se borra al final de cada cuatrimestre, guardar en el home la lista de dependencias (`requirements.txt` o `pyproject.toml`) para poder recrear el entorno.

PyTorch instalado con `uv pip install torch` ya incluye las librerías de CUDA que necesita.

