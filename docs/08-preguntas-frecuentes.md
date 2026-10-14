# Preguntas frecuentes

## Al conectarme por SSH aparece "REMOTE HOST IDENTIFICATION HAS CHANGED"

SSH guarda la identidad de cada máquina a la que se conecta y avisa si cambia. Esto puede pasar cuando la máquina asignada se reinstala. Para borrar la identidad guardada, correr en su computadora:

```
ssh-keygen -R labs004.udesa.edu.ar
```

Al volver a conectarse, SSH pide confirmar la nueva identidad. Si el aviso aparece sin que haya habido una reinstalación anunciada, reportarlo a soporte-s004@udesa.edu.ar.
