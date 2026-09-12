# Software 

Actualmente las maquinas cuentan con software de desarrollo global para todos los usuarios, entre ellos
- Visual Studio Code
- Python 
- GNU Toolchains

## Software instalado
**TODO** (Esto tiene que llenarse con lo de ansible)

## Sistema de modulos
- **Módulos (Lmod)**: la forma normal de acceder al software de cada
  curso. Comandos básicos:
  - `module avail` — lista lo disponible.
  - `module load <nombre-del-curso>` — activa el entorno de ese curso.
  - `module list` — qué tenés cargado en tu sesión actual.
  - `module unload <nombre>` / `module purge` — para sacar módulos.
- **Contenedores**: en general **no vas a usar `podman` ni `docker`
  directamente**. El software de cada curso que lo necesita ya viene
  envuelto detrás de `module load <curso>` — el comando que ves siempre es
  el mismo, sin importar qué corre por debajo.
- **Cursos con GPU/hardware físico**: si tu curso usa GPU, herramientas
  gráficas y hardware USB conectado a la máquina a la vez, hay un wrapper
  específico para eso. Si desconectás y reconectás el hardware en medio de
  una sesión, vas a tener que reiniciar ese entorno — es un límite
  conocido, no un error tuyo.
- **Verificación de GPU**: si sospechás que la GPU no está funcionando
  bien en una máquina, existe un script de autodiagnóstico
  (`gpu-selftest.sh`) que corre el equipo de soporte — reportalo si algo
  falla, no hace falta que lo corras vos.


## Solicitud de software
