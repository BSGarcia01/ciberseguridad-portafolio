# Administración y seguridad de Linux — Laboratorios 07 al 10

**Área:** Linux, Blue Team y fundamentos de Cloud Security  
**Entorno:** Kali Linux en VirtualBox sobre macOS  
**Nivel:** Principiante  
**Tipo de actividad:** Laboratorios prácticos educativos

## Objetivo general

Desarrollar habilidades básicas de administración de identidades, control de acceso, monitoreo de procesos y análisis de registros de actividad en sistemas Linux.

---

## Laboratorio 07 — Usuarios y grupos

### Objetivo

Identificar el usuario actual, su grupo principal y sus grupos adicionales.

### Comandos utilizados

```bash
whoami
id
groups
```

### Resultados obtenidos

- Usuario: `kali`
- UID: `1000`
- GID principal: `1000`

Grupos identificados:

```text
kali adm dialout cdrom floppy sudo audio dip video
plugdev users scanner wireshark kaboxer vboxsf
bluetooth netdev lpadmin
```

### Aprendizaje

Los grupos permiten administrar permisos colectivamente. En un entorno empresarial, pueden utilizarse para organizar usuarios según sus departamentos y responsabilidades.

Comprendí que pertenecer al grupo `sudo` no significa ejecutar permanentemente todas las acciones con privilegios administrativos.

---

## Laboratorio 08 — Propietarios y grupos

### Objetivo

Modificar el grupo propietario de un archivo y verificar los cambios realizados.

### Comandos utilizados

```bash
cd /home/kali/laboratorio-linux

touch permisos-grupos.txt

ls -l permisos-grupos.txt

chgrp users permisos-grupos.txt

ls -l permisos-grupos.txt

chgrp kali permisos-grupos.txt

ls -l permisos-grupos.txt
```

### Resultados obtenidos

| Etapa | Propietario | Grupo |
|---|---|---|
| Configuración inicial | kali | kali |
| Después del cambio | kali | users |
| Después de restaurar | kali | kali |

### Aprendizaje y corrección conceptual

Durante la evaluación confundí inicialmente los comandos `chmod` y `chown`. Después del repaso comprendí sus diferencias:

- `chmod`: modifica permisos.
- `chgrp`: modifica el grupo propietario.
- `chown`: modifica el usuario propietario y, opcionalmente, el grupo.

En este laboratorio se practicó `chgrp`. El comando `chown` se estudió de manera conceptual.

---

## Laboratorio 09 — Monitoreo de procesos

### Objetivo

Identificar procesos en ejecución, consultar su consumo de recursos y finalizar un proceso de prueba de manera controlada.

### Comandos utilizados

```bash
ps
ps aux
top

sleep 300 &

LAB_PID=$!
echo "$LAB_PID"

ps -p "$LAB_PID" -o pid,user,%cpu,%mem,comm

kill "$LAB_PID"

ps -p "$LAB_PID"
```

### Resultados obtenidos

| Elemento | Resultado |
|---|---|
| Proceso | sleep |
| PID | 289636 |
| Usuario | kali |
| Consumo aproximado de CPU | 0.0 % |

Después de ejecutar `kill` y consultar nuevamente el PID, el proceso dejó de aparecer.

### Aprendizaje

Comprendí que cada proceso posee un identificador denominado PID y que es posible consultar sus recursos y el usuario asociado.

También aprendí que un consumo elevado de CPU no demuestra necesariamente la existencia de un ataque informático.

Antes de finalizar un proceso desconocido, es necesario investigar su función y el impacto que podría generar su interrupción.

---

## Laboratorio 10 — Análisis de logs

### Objetivo

Consultar registros del sistema, identificar mensajes de error e interpretar eventos desde una perspectiva de seguridad.

### Comandos utilizados

```bash
journalctl -n 10 --no-pager

journalctl -b -n 15 --no-pager

journalctl -b -p err -n 10 --no-pager
```

### Evento 1 — Inicio de un servicio

Registro observado:

```text
Nov 17 17:30:44 kali systemd[897]: Starting xdg-document-portal.service - flatpak document portal service...
```

Interpretación:

El sistema registró el inicio de un servicio relacionado con la gestión del acceso a documentos desde aplicaciones aisladas.

El mensaje no constituye por sí mismo evidencia de un problema de seguridad.

### Evento 2 — Error de virtualización gráfica

Registro observado:

```text
Nov 17 17:28:47 kali kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* vmwgfx seems to be running on an unsupported hypervisor.
```

Interpretación:

El controlador gráfico detectó un entorno de virtualización que considera no compatible.

Durante el análisis se encontraron reportes similares relacionados con VirtualBox y Kali Linux.

El evento se clasificó preliminarmente como un problema de compatibilidad técnica. No se confirmó la causa exacta ni se modificó la configuración gráfica.

### Aprendizaje y correcciones

Inicialmente no observé diferencias claras al utilizar la opción `-b`. Durante la revisión comprendí que esta opción limita la consulta al arranque actual.

También aprendí que múltiples intentos fallidos de autenticación pueden indicar actividad sospechosa, pero no permiten confirmar un ataque sin información adicional.

Es necesario investigar el contexto antes de clasificar un evento como incidente de seguridad.

---

## Competencias desarrolladas

- Identificación de usuarios y grupos.
- Administración básica de grupos propietarios.
- Diferenciación de permisos y propietarios.
- Identificación y monitoreo de procesos.
- Finalización controlada de procesos de prueba.
- Consulta de registros mediante journalctl.
- Interpretación inicial de eventos del sistema.
- Diferenciación entre señales sospechosas y evidencia de ataques.

## Referencias consultadas

- Documentación de journalctl: https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- Registro de errores de Kali Linux: https://bugs.kali.org/view.php?id=9097
- Reporte de VirtualBox: https://github.com/VirtualBox/virtualbox/issues/67

## Conclusión

Estos laboratorios me permitieron adquirir conocimientos iniciales de administración y seguridad de Linux, fundamentales para continuar mi formación en Blue Team y Cloud Security.

Comprendí la importancia de verificar configuraciones, analizar evidencias y evitar conclusiones precipitadas durante una investigación técnica.

**Nota:** todas las prácticas se realizaron en una máquina virtual propia con fines educativos.
