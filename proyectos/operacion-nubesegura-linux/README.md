# Proyecto integrador — Operación NubeSegura

**Área:** Administración y seguridad de Linux  
**Entorno:** Kali Linux, VirtualBox y macOS  
**Tipo de proyecto:** Simulación empresarial educativa  
**Fecha:** 17 de noviembre de 2026

## 1. Objetivo

Aplicar los conocimientos adquiridos durante mi formación inicial en Linux mediante una simulación de administración y protección de recursos empresariales.

El proyecto integra administración de archivos, permisos, usuarios, grupos, procesos y análisis de registros del sistema.

## 2. Escenario

NubeSegura es una empresa ficticia que necesita organizar documentos confidenciales, implementar controles de acceso y monitorear un sistema Linux.

Todas las actividades se realizaron en una máquina virtual propia, utilizando información ficticia.

## 3. Reconocimiento del sistema

Mediante los comandos `id` y `groups` identifiqué la información del usuario y sus grupos.

Resultados:

- Usuario: kali
- UID: 1000
- GID principal: 1000
- Directorio personal: /home/kali

## 4. Administración de archivos

Creé una estructura de directorios destinada a organizar información confidencial, reportes y evidencias.

```text
evaluacion-linux/
├── confidencial/
│   └── clientes.txt
├── evidencias/
└── reportes/
    └── auditoria.txt
```

La estructura representa los recursos principales solicitados en el ejercicio.

Utilicé comandos como `mkdir`, `cd`, `touch`, `echo`, `cat` y `ls`.

## 5. Implementación y verificación de controles de acceso

Apliqué el principio de mínimo privilegio mediante permisos específicos para cada recurso.

| Recurso | Permisos | Objetivo |
|---|---|---|
| confidencial | 700 | Acceso ordinario exclusivo del propietario |
| clientes.txt | 600 | Lectura y escritura para el propietario |
| auditoria.txt | 640 | Lectura y escritura para el propietario y lectura para el grupo |

### Evidencia final

```text
700 drwx------ confidencial
600 -rw------- confidencial/clientes.txt
640 -rw-r----- reportes/auditoria.txt
```

Los resultados fueron verificados mediante el comando `stat`.

## 6. Administración de grupos

Durante la evaluación inicial practiqué el cambio del grupo propietario de un recurso.

| Etapa | Propietario | Grupo |
|---|---|---|
| Inicial | kali | kali |
| Modificado | kali | users |
| Restaurado | kali | kali |

Utilicé `chgrp` para modificar el grupo y `ls -ld` para verificar los cambios.

Esta práctica se realizó sobre un directorio creado inicialmente por error. Posteriormente corregí su tipo y permisos durante la recuperación.

## 7. Monitoreo de procesos

Creé un proceso de prueba utilizando:

```bash
sleep 300 &
LAB_PID=$!
echo "$LAB_PID"
```

PID identificado: 37168.

Finalicé el proceso mediante:

```bash
kill "$LAB_PID"
ps -p "$LAB_PID"
```

El sistema confirmó la terminación del proceso y la consulta posterior no mostró procesos asociados al PID.

Durante la práctica confundí las opciones `-u` y `-o` del comando `ps`. Esta diferencia fue revisada posteriormente. La identificación detallada del consumo de CPU quedó como ejercicio de refuerzo.

## 8. Análisis de registros

Consulté registros del sistema mediante `journalctl`.

Uno de los eventos observados fue:

```text
Nov 17 19:09:16 kali systemd[1]: phpsessionclean.service: Deactivated successfully.
```

Este registro informa sobre la desactivación correcta del servicio de limpieza de sesiones PHP.

Aprendí que el nombre del equipo, el PID y la identidad del usuario representan conceptos diferentes.

Asimismo, comprendí que múltiples intentos fallidos de autenticación requieren investigar su contexto antes de confirmar un ataque.

## 9. Dificultades y soluciones

| Dificultad | Solución o aprendizaje |
|---|---|
| Creación de un directorio en lugar de un archivo | Diferenciar mkdir de touch |
| Configuración incorrecta de permisos 620 | Revisar los valores de lectura y escritura y aplicar 640 |
| Falta de verificación de permisos | Utilizar stat para comprobar los resultados |
| Confusión entre opciones de ps | Estudiar la diferencia entre selección de procesos y formato de salida |
| Confusión entre hostname, PID y usuario | Reforzar la interpretación de registros |

## 10. Resultados de la evaluación

- Evaluación inicial autónoma: 78/100.
- Calificación acumulada después de la recuperación guiada: 92/100.

Estas calificaciones corresponden a una evaluación educativa, no a una certificación oficial.

## 11. Conclusiones

Este proyecto me permitió aplicar conocimientos básicos de seguridad y administración de Linux en un entorno controlado.

Logré implementar y verificar controles de acceso, administrar grupos propietarios, identificar procesos y realizar consultas de registros del sistema.

Identifiqué también oportunidades de mejora en el monitoreo de recursos y la interpretación de logs.

Estos conocimientos constituyen una base para continuar mi formación en redes y Cloud Security.
