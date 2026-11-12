# Fundamentos de Linux — Laboratorios 02 al 06

**Área:** Linux y fundamentos de ciberseguridad  
**Sistema utilizado:** Kali Linux en VirtualBox  
**Nivel:** Principiante  
**Estado:** Prácticas realizadas y documentadas

## Objetivo general

Aprender a utilizar comandos básicos de Linux, administrar archivos y directorios, interpretar permisos y aplicar controles de acceso siguiendo el principio de mínimo privilegio.

Estos ejercicios forman parte de mi preparación para especializarme en Cloud Security.

---

## Laboratorio 02 — Exploración del sistema

### Objetivo

Identificar el usuario actual, conocer la ubicación dentro del sistema de archivos y explorar el contenido de los directorios.

### Comandos utilizados

```bash
whoami
pwd
ls
ls -la
```

### Resultados obtenidos

**Usuario identificado:**

```text
kali
```

**Directorio de trabajo:**

```text
/home/kali
```

**Contenido visible del directorio:**

```text
Desktop  Documents  Downloads  Music
Pictures  Projects  Public  Templates  Videos
```

Al ejecutar `ls -la` observé información adicional, como permisos, propietarios, fechas y archivos ocultos cuyos nombres comienzan con un punto.

### Aprendizaje

Comprendí cómo identificar mi usuario, consultar mi ubicación y distinguir entre archivos visibles y ocultos.

También aprendí que un archivo oculto no necesariamente está protegido contra accesos no autorizados.

---

## Laboratorio 03 — Creación de archivos y directorios

### Objetivo

Aprender a organizar información desde la terminal de Linux.

### Comandos utilizados

```bash
cd /home/kali

mkdir laboratorio-linux
cd laboratorio-linux

mkdir evidencias reportes

cd reportes
touch informe.txt

echo "Mi primer laboratorio de Linux" > informe.txt
cat informe.txt
```

### Estructura del laboratorio

```text
laboratorio-linux/
├── evidencias/
└── reportes/
    └── informe.txt
```

### Aprendizaje

- `mkdir` permite crear directorios.
- `cd` permite desplazarse entre directorios.
- `touch` puede crear archivos vacíos.
- `echo` permite generar texto.
- `cat` permite consultar el contenido de un archivo.
- `pwd` permite verificar la ubicación actual.

Aprendí que es importante comprobar los resultados de los comandos y mantener una estructura organizada para los archivos de trabajo.

---

## Laboratorio 04 — Permisos básicos

### Objetivo

Comprender los permisos de lectura, escritura y ejecución en Linux.

### Comando estudiado

```bash
chmod 600 informe.txt
```

### Interpretación

Los permisos `600` representan:

| Categoría | Valor | Permisos |
|---|---|---|
| Propietario | 6 | Lectura y escritura |
| Grupo | 0 | Ninguno |
| Otros | 0 | Ninguno |

Representación simbólica:

```text
-rw-------
```

### Aprendizaje

Comprendí que conceder permisos excesivos puede poner en riesgo la confidencialidad e integridad de la información.

También aprendí que el principio de mínimo privilegio consiste en otorgar únicamente los accesos necesarios.

---

## Laboratorio 05 — Verificación de permisos

### Objetivo

Aplicar permisos específicos y comprobar que el sistema los haya establecido correctamente.

### Comandos utilizados

```bash
cd /home/kali/laboratorio-linux/reportes

touch configuracion.txt

chmod 640 configuracion.txt

ls -l configuracion.txt
stat configuracion.txt
```

### Resultados obtenidos

**Permisos:**

```text
0640/-rw-r-----
```

**Usuario propietario:** `kali`

**Grupo propietario:** `kali`

### Interpretación

- El propietario puede leer y modificar el archivo.
- Los miembros del grupo tienen permiso de lectura.
- Los demás usuarios no reciben permisos de acceso al archivo.

### Aprendizaje

Aprendí que ejecutar un comando no es suficiente para garantizar que una configuración haya quedado correctamente aplicada.

Es importante utilizar herramientas como `stat` o `ls -l` para verificar el resultado.

---

## Laboratorio 06 — Seguridad de directorios

### Objetivo

Comprender los permisos de directorios y proteger una carpeta privada.

### Comandos utilizados

```bash
cd /home/kali/laboratorio-linux

mkdir carpeta-confidencial

ls -ld carpeta-confidencial

chmod 700 carpeta-confidencial

ls -ld carpeta-confidencial

touch carpeta-confidencial/prueba.txt

ls -la carpeta-confidencial
```

### Permisos originales

```text
drwxrwxr-x
```

Valor numérico: `775`.

### Permisos después de aplicar el control

```text
drwx------
```

Valor numérico: `700`.

### Interpretación

La configuración original otorgaba permisos completos al propietario y al grupo, además de lectura y acceso al directorio para otros usuarios.

Después del cambio, únicamente el propietario conserva los permisos ordinarios de lectura, escritura y acceso al directorio.

### Aprendizaje

Comprendí que el permiso `x` tiene significados diferentes:

- En archivos, permite su ejecución cuando corresponde.
- En directorios, permite atravesarlos y acceder a entradas conocidas, sujeto a los demás permisos.

Aprendí también que proteger una carpeta no significa que todos sus archivos internos tengan automáticamente los mismos permisos.

---

## Conclusiones generales

Durante estos cinco laboratorios desarrollé habilidades iniciales para:

1. Identificar usuarios y rutas en Linux.
2. Navegar por el sistema de archivos.
3. Crear y organizar directorios y archivos.
4. Interpretar permisos mediante notación simbólica y numérica.
5. Modificar permisos con `chmod`.
6. Verificar configuraciones utilizando `stat` y `ls`.
7. Aplicar el principio de mínimo privilegio.

Estas habilidades constituyen una base para continuar aprendiendo administración y seguridad de servidores Linux utilizados en entornos cloud.

## Próximos temas

- Administración de usuarios y grupos.
- Propietarios de archivos y directorios.
- Procesos y servicios.
- Registros de actividad del sistema.
- Fundamentos de redes.
- Seguridad de servidores en la nube.

---

**Nota:** todos los ejercicios se realizaron con fines educativos en una máquina virtual propia. Los resultados presentados corresponden a las observaciones registradas durante las prácticas, y las representaciones explicativas se indican como tales.
