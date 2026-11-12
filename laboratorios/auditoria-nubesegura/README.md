# Laboratorio 01 — Auditoría básica de seguridad: NubeSegura

**Área:** Fundamentos de ciberseguridad  
**Tipo de actividad:** Simulación educativa  
**Nivel:** Principiante  
**Estado:** Completado

## 1. Objetivo

Identificar vulnerabilidades y riesgos de seguridad en una empresa ficticia, analizar su impacto sobre la confidencialidad, integridad y disponibilidad de la información, y proponer controles de seguridad.

## 2. Descripción del escenario

NubeSegura S.A.S. es una empresa ficticia que almacena información personal de 2.000 clientes.

Durante una auditoría simulada se presentan tres hallazgos:

- Una base de datos accesible públicamente sin autenticación.
- Una cuenta administrativa compartida entre varios empleados.
- Ausencia de copias de seguridad.

**Alcance:** análisis teórico de los escenarios proporcionados. No se realizaron pruebas de penetración, escaneos ni inspecciones sobre sistemas reales.

## 3. Hallazgo A: Base de datos expuesta públicamente

**Activo afectado:** información personal de clientes.

**Vulnerabilidad:** acceso público sin autenticación.

**Riesgo identificado:** una persona no autorizada podría acceder a información confidencial, extraerla y utilizarla para cometer fraudes o venderla.

**Principio CIA principalmente afectado:** confidencialidad.

### Controles recomendados

- Restringir el acceso público a la base de datos.
- Implementar mecanismos de autenticación y autorización.
- Aplicar el principio de mínimo privilegio.
- Registrar y supervisar los accesos.
- Revisar si existen indicios de accesos no autorizados.

**Prioridad orientativa:** crítica, debido a la exposición directa de información personal.

## 4. Hallazgo B: Cuenta administrativa compartida

**Activo afectado:** sistemas y cuentas de administración.

**Vulnerabilidad:** varios administradores utilizan las mismas credenciales.

**Riesgo identificado:** dificultad para atribuir acciones a una persona concreta, accesos no autorizados y posible uso indebido de privilegios.

**Principios CIA potencialmente afectados:** confidencialidad, integridad y disponibilidad, según las acciones realizadas.

### Controles recomendados

- Crear cuentas individuales para los administradores.
- Implementar autenticación multifactor (MFA).
- Asignar permisos según las funciones de cada usuario.
- Mantener registros de auditoría.
- Eliminar cuentas compartidas innecesarias.

**Prioridad orientativa:** alta.

## 5. Hallazgo C: Ausencia de copias de seguridad

**Activo afectado:** información y sistemas necesarios para la operación.

**Vulnerabilidad:** inexistencia de un mecanismo de respaldo y recuperación.

**Riesgo identificado:** pérdida de información y dificultad para restablecer las operaciones después de fallas, errores humanos o incidentes de seguridad.

**Principio CIA principalmente afectado:** disponibilidad. La integridad también puede verse afectada en determinados incidentes.

### Controles recomendados

- Establecer copias de seguridad periódicas.
- Mantener copias protegidas y separadas de los sistemas originales.
- Definir una política de conservación de respaldos.
- Realizar pruebas de restauración.
- Documentar un procedimiento de recuperación.

**Prioridad orientativa:** alta.

## 6. Resumen de hallazgos

| Hallazgo | Principal riesgo | Prioridad orientativa |
|---|---|---|
| Base de datos pública | Exposición de información personal | Crítica |
| Cuenta administrativa compartida | Acceso indebido y falta de trazabilidad | Alta |
| Ausencia de respaldos | Pérdida de información y continuidad operativa | Alta |

Las prioridades son estimaciones académicas basadas en el escenario. Una evaluación empresarial real requeriría información adicional sobre impacto, probabilidad y controles existentes.

## 7. Lecciones aprendidas

Durante este laboratorio aprendí a:

- Diferenciar activos, amenazas, vulnerabilidades y riesgos.
- Aplicar la tríada CIA a escenarios empresariales.
- Reconocer la importancia del principio de mínimo privilegio.
- Comprender por qué las cuentas administrativas deben ser individuales.
- Identificar la importancia de MFA.
- Entender que realizar respaldos no es suficiente si no se comprueba su restauración.
- Proponer medidas de seguridad a partir de riesgos identificados.

## 8. Conclusión

Este ejercicio me permitió comprender que la ciberseguridad no consiste únicamente en utilizar herramientas técnicas, sino también en identificar riesgos, analizar sus consecuencias y recomendar medidas de protección.

Como estudiante de Ingeniería de Sistemas y en formación en ciberseguridad, este laboratorio representa una primera experiencia de análisis defensivo y documentación técnica.

**Nota:** todos los escenarios son ficticios y se utilizan exclusivamente con fines educativos.
