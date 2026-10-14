# Tips de SSH

## Copiar archivos (scp)

Para copiar archivos entre su computadora y el laboratorio, usar `scp` desde una terminal de **su computadora** (no desde la sesión SSH), con la VPN conectada. Cada `scp` cuenta para el [límite de conexiones simultáneas](02-acceso.md#acceso-remoto-por-ssh): si tienen dos sesiones abiertas, deben cerrar una antes de transferir archivos.

Subir un archivo o una carpeta (`-r`) al laboratorio:

```
scp archivo.txt <usuario>@labs004.udesa.edu.ar:~/
scp -r carpeta/ <usuario>@labs004.udesa.edu.ar:~/scratch/
```

Descargar un archivo o una carpeta del laboratorio al directorio actual:

```
scp <usuario>@labs004.udesa.edu.ar:~/resultados.csv .
scp -r <usuario>@labs004.udesa.edu.ar:~/scratch/work/resultados .
```

Los archivos grandes (datasets, checkpoints) deben ir a `~/scratch` por la [cuota del home](04-almacenamiento.md). Como `~/scratch` es local a cada máquina, los archivos quedan en la misma máquina a la que los asigna la conexión SSH.

## Interfaz gráfica (X11 forwarding)
Una de las capacidades de la conexión por SSH es renderizar una interfaz gráfica dentro de la máquina y visualizar en la máquina local. Para ello, deben conectarse como:

```
ssh -XYC <usuario>@labs004.udesa.edu.ar
```

El reenvío de interfaz gráfica solo está soportado desde clientes Linux.
