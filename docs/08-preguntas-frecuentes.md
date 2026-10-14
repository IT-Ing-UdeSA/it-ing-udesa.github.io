# Preguntas frecuentes

## Al conectarme por SSH aparece "REMOTE HOST IDENTIFICATION HAS CHANGED"

SSH guarda la identidad de cada máquina a la que se conecta y avisa si cambia. Esto puede pasar cuando la máquina asignada se reinstala. Para borrar la identidad guardada, correr en su computadora:

```
ssh-keygen -R labs004.udesa.edu.ar
```

Al volver a conectarse, SSH pide confirmar la nueva identidad. Si el aviso aparece sin que haya habido una reinstalación anunciada, reportarlo a soporte-s004@udesa.edu.ar.

## La contraseña se acepta, pero la conexión se cierra enseguida

```
<usuario>@labs004.udesa.edu.ar's password:
Connection closed by 172.23.20.251 port 22
```

Si esto pasa de lunes a viernes entre las 07:00 y las 22:00, es porque el acceso remoto está fuera de horario (ver [Horarios de acceso remoto](02-acceso.md#horarios-de-acceso-remoto)). Lo mismo ocurre con `scp`, `sftp` y `rsync`.

Una contraseña incorrecta se ve distinto: SSH la vuelve a pedir con `Permission denied, please try again.`

Si pasa en un feriado, puede que ese día no esté cargado en la lista de feriados que mantiene el equipo de IT. En ese caso rige el horario de lunes a viernes.

## Se cortó mi sesión a las 07:00

De lunes a viernes, las sesiones remotas se cortan a las 07:00 (ver [Horarios de acceso remoto](02-acceso.md#horarios-de-acceso-remoto)). A las 06:50 aparece este aviso en la terminal:

```
*** AVISO: el acceso SSH al laboratorio cierra a las 07:00 (lunes a viernes,
*** horario de clases). Tu sesion se va a cortar en 10 minutos.
*** Guarda tu trabajo. Se puede volver a entrar a partir de las 22:00.
```

Lo que corre dentro de tmux sigue vivo hasta el reinicio de las máquinas de las 07:30 (ver [Disponibilidad y mantenimiento](07-acuerdo-de-nivel-de-servicio.md#6-disponibilidad-y-mantenimiento)).
