# Almacenamiento

Cada máquina tiene dos tipos de almacenamiento:

- **Disco local**: NVMe de 1 TB, propio de cada máquina. Contiene el sistema operativo y `/scratch`.
- **NFS**: almacenamiento de red, compartido por las 22 máquinas. Contiene los `$HOME` de los usuarios y `$DATA`.

## Estructura de directorios

```
/
├── home/
│   └── <usuario>/                   $HOME (NFS)
│       ├── scratch -> /scratch/<usuario>
│       ├── Downloads -> ~/scratch/downloads
│       └── .local/share/Trash/      papelera (cuenta para la cuota)
├── scratch/
│   └── <usuario>/                   disco local
│       ├── downloads/
│       └── work/                    entornos virtuales, proyectos
├── opt/
│   └── modules/                     software del laboratorio (solo lectura)
│       └── modulefiles/
└── <PLACEHOLDER: ruta de $DATA>     NFS
```

## Detalle de cada directorio

| Directorio | Dónde vive | Tamaño | Persistencia | Visible desde otras máquinas | Uso |
|---|---|---|---|---|---|
| `/home/<usuario>` (`$HOME`) | NFS | 2 GB y 25.000 archivos por usuario | Persistente | Sí | Código fuente, configuración, apuntes |
| `/scratch/<usuario>` (`~/scratch`) | Disco local (NVMe 1 TB) | Sin cuota; limitado por el espacio libre del disco `<PLACEHOLDER: espacio libre aproximado>` | Se purgan los archivos con más de 14 días; se borra al reinstalar la máquina | No | Datasets, entornos de conda/Python, cachés, checkpoints, contenedores |
| `~/scratch/downloads` (`~/Downloads`) | Disco local | Comparte el espacio de `~/scratch` | Igual que `~/scratch` | No | Descargas |
| `/opt/modules` | `<PLACEHOLDER: disco local o NFS>` | — | Persistente, solo lectura | Sí | Software y módulos de los cursos (`module load`) |
| `$DATA` | NFS | `<PLACEHOLDER: tamaño y cuota>` | `<PLACEHOLDER: persistencia y backup>` | Sí | `<PLACEHOLDER: para qué se usa y quién tiene acceso>` |

`<PLACEHOLDER: política de backup de $HOME>`

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
