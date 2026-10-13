# Acuerdo de Nivel de Servicio (SLA)

```{note}
Este documento describe el nivel de servicio que el equipo se compromete a brindar
a los usuarios del laboratorio.
```

## 1. Uso aceptable del laboratorio

- Las máquinas están destinadas a **fines académicos**: cursada,
  trabajos prácticos y trabajos de tesis autorizados.
- No está permitido el uso de las máquinas para cómputo de alto
  rendimiento no autorizado, o procesos de larga duración que
  degraden el servicio para demas usuarios.

## 2. Responsabilidades del usuario

- Mantener el uso de `home` dentro de la cuota (2 GB / 25.000 archivos),
  usando `~/scratch` para datasets, software local y cachés.
- No depender de `~/scratch` para nada que no pueda perderse.
- Reportar fallas de hardware al equipo de soporte (ticketsti@udesa.edu.ar)
- Usar los canales oficiales de soporte para cualquier reclamo, de forma
  de garantizar trazabilidad y tiempos de respuesta.

## 3. Alcance

Este acuerdo cubre:

- Las **22 máquinas de uso general** del laboratorio (físicas y por conexión
  remota), descriptas en [Máquinas](01-que-es-este-laboratorio.md).
- El sistema de **cuentas de usuario**, **directorios** (`home` y
  `~/scratch`) y **cuotas**.
- El **software provisto** a través del sistema sistema de modulos y los contenedores

No cubre software o hardware personal de los usuarios, ni proyectos de
cómputo intensivo de larga duración.

## 4. Soporte: horarios y canales

| | |
|---|---|
| **Canal principal** | soporte-s004@udesa.edu.ar |
| **Horario de atención** | Lunes a viernes, 9:00–18:00 |

Las solicitudes hechas por canales no oficiales (mensajes personales,
grupos de curso, etc.) no tienen garantía de respuesta ni de tiempo de
resolución. Toda solicitud de software específico o reporte de problema
debe canalizarse por el mail de soporte, indicando:

- Nombre de usuario y máquina afectada (ej. `labo-s004-05`).
- Curso o proyecto asociado.
- Descripción del problema.

## 5. Tiempos de respuesta y escalamiento (DETALLAR)

Dado que el laboratorio se encuentra en una **fase experimental**
(ver aviso en la [portada](index.md)), los tiempos abajo son objetivos, no
garantías contractuales, hasta que el proyecto salga de esa fase.

Nota; Detallar que el tiempo promedio de respuesta es de un dia.

| Nivel | Descripción | Tiempo objetivo |
|---|---|---|
| **Nivel 1** | Soporte de laboratorio (cuentas, acceso, cuotas, software ya instalado) | **[COMPLETAR: ej. 2 días hábiles]** |
| **Nivel 2** | Coordinación del laboratorio / instalación de software nuevo | **[COMPLETAR: ej. +2 días hábiles]** |
| **Nivel 3** | Proveedor externo o soporte central de IT de la universidad | **[COMPLETAR]** |

Incidentes que impiden el dictado de una clase (ej. caída total del acceso
remoto o de un aula) tienen prioridad sobre el resto de las solicitudes.

## 6. Disponibilidad y mantenimiento

- **Máquinas físicas**: se mantienen operativas durante el horario de
  clases. Reinstalaciones o reimágenes se comunican con anticipación
  cuando es posible
- Todos los dias a las 8am y tambien al momento de iniciar una clase, se
  cerrara la sesion a cada usuario que se encuentre conectado. El laboratio no
  esta pensado para tener sesiones abiertas por mucho tiempo.
- **`home` de usuario**: persistente entre las 22 máquinas, con cuota de
  **2 GB / 25.000 archivos** por usuario.
- **Ventanas de mantenimiento programado**: El primero de cada mes durante
  horario nocturno
- **Actualizaciones de seguridad**: pueden aplicarse fuera de las
  ventanas programadas cuando se trata de vulnerabilidades críticas.

## 7. Solicitud e instalación de software

- Las solicitudes de software nuevo o específico de un curso se envían a
  soporte-s004@udesa.edu.ar con la mayor anticipación posible antes del
  inicio del cuatrimestre.
- **Fecha límite de solicitud**: **[COMPLETAR: ej. fin de cuatrimestre
  anterior]**.
- **Ventana de pruebas** (a cargo del docente que solicita el software):
  **[COMPLETAR]**.
- **Fecha de "congelamiento"** de la imagen del curso, luego de la cual
  solo se aplican correcciones de seguridad o bugs bloqueantes:
  **[COMPLETAR]**.
- El software de cada curso se distribuye mediante módulos (`module load
  <curso>`), no por instalación manual de cada usuario.


## 8. Revisión del acuerdo

Este SLA se revisa antes del inicio del ciclo lectivo. Cualquier cambio en
los compromisos de tiempo de respuesta o disponibilidad se comunica a los
usuarios a través de esta wiki.
