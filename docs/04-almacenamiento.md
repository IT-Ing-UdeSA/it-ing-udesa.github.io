# Almacenamiento

Cada máquina tiene dos tipos de almacenamiento:

- **Disco local**: NVMe de 1 TB, propio de cada máquina. Contiene el sistema operativo y `/scratch`.
- **NFS**: almacenamiento de red, compartido por las 22 máquinas. Contiene los `$HOME` de los usuarios.

## Estructura de directorios

```
/
├── home/
│   └── <usuario>/                   $HOME (NFS)
│       ├── scratch -> /scratch/<usuario>
│       ├── Downloads -> ~/scratch/downloads
└── scratch/
    └── <usuario>/                   disco local
        ├── downloads/
        └── work/                    entornos virtuales, proyectos
```

## Detalle de cada directorio

| Directorio | Dónde vive | Tamaño | Persistencia | Visible desde otras máquinas | Uso |
|---|---|---|---|---|---|
| `/home/<usuario>` (`$HOME`) | NFS | 2 GB y 25.000 archivos por usuario | Persistente | Sí | Código fuente, configuración, apuntes |
| `/scratch/<usuario>` (`~/scratch`) | Disco local (NVMe 1 TB) | Sin cuota; limitado por el espacio libre del disco | Se borra al final de cada cuatrimestre y al reinstalar la máquina | No | Datasets, entornos de conda/Python, cachés, checkpoints |
| `~/scratch/downloads` (`~/Downloads`) | Disco local | Comparte el espacio de `~/scratch` | Igual que `~/scratch` | No | Descargas |

## Sistema de cuotas en home

Cada $HOME de cada usuario tiene un límite de **2 GB y 25.000 archivos**. Este espacio tiene
como objetivo guardar información liviana (códigos, imágenes, etc.).
Al acercarse al límite, el comando `quota` les muestra el uso actual, y también
aparece un resumen al iniciar sesión. Si superan el límite, van a dejar de
poder guardar archivos nuevos ahí hasta que liberen espacio.
