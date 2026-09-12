# Directorios

**Esto es lo más importante de todo este documento.**

Tenés **tres lugares** distintos donde puede vivir un archivo tuyo en estas
máquinas, y **se comportan completamente distinto**:

| Lugar | ¿Se guarda? | ¿Te sigue a otra máquina? | ¿Tiene límite de tamaño? | Para qué usarlo |
|---|---|---|---|---|
| **Tu home** (`~` o `/home/tu-usuario`) | **Sí, persistente** | **Sí** — es el mismo en las 23 máquinas | **Sí — 2 GB** y hasta 25.000 archivos | Código fuente, configuración, apuntes, lo que necesites conservar |
| **`~/scratch`** (= `/scratch/tu-usuario`) | **NO** — se borra en cada reinstalación de la máquina, y además se purga automáticamente cada 14 días | **NO** — es local a *esa* máquina específica | No — capacidad libre del disco | Datasets grandes, entornos de conda/Python, cachés de modelos, checkpoints de entrenamiento, contenedores |
| **`/opt/modules`** | Sí, pero es de solo lectura | Sí | — | Software y módulos del curso — no se escribe ahí, solo se usa |

## La regla simple

> **Si lo necesitás la semana que viene, o en otra máquina: va en tu
> home.**
> **Si es descartable, o es más grande que 2 GB, o es una caché: va en
> `~/scratch`.**

**`~/scratch` NO ES UN BACKUP DE NADA.** Es capacidad de disco local que se
te da gratis porque cada máquina tiene NVMe de sobra, pero:

- se **borra completamente** la próxima vez que esa máquina se reinstale
  (puede pasar sin previo aviso para vos, por mantenimiento),
- se **purga automáticamente** cualquier archivo con más de 14 días,
- **no existe en ninguna otra máquina** — lo que dejaste en
  `labo-s004-05` no está en `labo-s004-12`.

Vas a ver un aviso de esto **cada vez que iniciás sesión** (mensaje del
día). No es un aviso genérico — leelo, en serio.

## Tu carpeta de Descargas

`~/Downloads` también es en realidad un acceso directo a
`~/scratch/downloads` — mismo trato: local, temporal, no persistente. Si
descargás algo que necesitás conservar, **movelo a tu home** antes de que
pase mucho tiempo o cambies de máquina.

**Ojo con Firefox**: si tu máquina tiene la versión "snap" de Firefox
(la que viene por defecto en Ubuntu), las descargas del navegador **no**
respetan este acceso directo — van a una carpeta interna del snap sin que
lo notes. Si no estás seguro de cuál versión de Firefox tiene tu máquina,
preguntale al equipo de soporte.

## Tu cuota de home

Tu home tiene un límite de **2 GB y 25.000 archivos**. Si te acercás al
límite, `quota` (en la terminal) te muestra el uso actual, y también
aparece un resumen al iniciar sesión. Si superás el límite, vas a dejar de
poder guardar archivos nuevos ahí hasta que liberes espacio — mové lo que
no necesites permanente a `~/scratch`, o borralo.

Un motivo típico de quedarte sin cuota sin darte cuenta: crear un entorno
de conda o un `node_modules` **dentro de tu home** en vez de en
`~/scratch`. Eso puede generar decenas de miles de archivos chicos por sí
solo. Las variables de entorno de este sistema (`CONDA_PKGS_DIRS`,
`PIP_CACHE_DIR`, etc.) ya están configuradas para evitar esto
automáticamente en la mayoría de los casos — pero si instalás algo por
fuera de esos mecanismos estándar, prestá atención a dónde cae.

Otras formas menos obvias de llenar la cuota sin darte cuenta:

- **La Papelera no es borrar.** Si borrás un archivo grande desde un
  gestor de archivos gráfico (no desde la terminal con `rm`), lo más
  probable es que vaya a la Papelera (`~/.local/share/Trash`) — que sigue
  estando dentro de tu home, y sigue contando contra tu cuota hasta que la
  vacíes de verdad.
- **Un entorno virtual de Python (`python3 -m venv`) creado dentro de tu
  home no es una caché** — es la instalación real de los paquetes que
  metas ahí adentro (torch, pandas, lo que sea), y puede pesar varios
  cientos de MB o más. Creá tus entornos virtuales dentro de
  `~/scratch/work/`, no en tu home.
- Lo mismo con paquetes instalados con `pip install --user` (van a
  `~/.local`) o extensiones acumuladas de VS Code — no son enormes de a
  una, pero suman con el tiempo.
- Si usás Node/npm, Rust/cargo, o Java/Maven/Gradle (el curso de Java):
  sus cachés (`~/.npm`, `~/.cargo`, `~/.m2`, `~/.gradle`) **ya están
  redirigidas** a `~/scratch` igual que las de pip/conda — no tenés que
  hacer nada. La única excepción real es el `target/` de un proyecto
  Rust/Java dentro de tu propio código (los artefactos de compilación de
  ESE proyecto puntual) — si un build individual pesa mucho, es por eso,
  no por la caché de dependencias.
