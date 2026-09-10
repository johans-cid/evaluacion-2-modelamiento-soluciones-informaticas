# Informe de Toma de Requerimientos
## Sistema de Creación de Tiques para Mesa de Ayuda — Consúltenos

---

## 1. Introducción

### 1.1 Propósito
El propósito de este documento es especificar los requerimientos funcionales y no funcionales del **Sistema de Creación de Tiques para Mesa de Ayuda**, solicitado por la consultora ficticia **Consúltenos**, con el fin de reemplazar el uso de planillas manuales y agilizar el seguimiento de los casos de atención a clientes.

### 1.2 Alcance
El sistema permitirá a los **ejecutivos de mesa de ayuda** registrar, derivar y cerrar tiques de atención generados por los clientes de la consultora. El **jefe de mesa** podrá supervisar el estado general de los tiques, revisar historiales y generar informes de gestión. Quedan fuera del alcance de esta primera versión la comunicación directa con el cliente final (portal de autoatención) y la integración con sistemas de facturación.

### 1.3 Definiciones, acrónimos y abreviaturas
- **Tique**: solicitud de atención registrada en el sistema, asociada a un cliente y un problema o requerimiento.
- **Ejecutivo**: usuario que crea, gestiona y da seguimiento a los tiques.
- **Jefe de mesa**: usuario con permisos de supervisión, asignación y generación de informes.
- **Criticidad**: nivel de urgencia asignado a un tique (ej. Alta, Media, Baja).
- **Estado del tique**: situación actual del tique dentro de su ciclo de vida (A resolución, Resuelto, No aplicable).

---

## 2. Descripción general

### 2.1 Perspectiva del producto
El sistema es una aplicación independiente que digitaliza un proceso hoy realizado en planillas Excel. No reemplaza otros sistemas de la consultora, pero podría integrarse a futuro con un sistema de correo o notificaciones.

### 2.2 Funciones generales
- Creación de tiques con datos del cliente, tipo de solicitud, criticidad, detalle y área asignada.
- Derivación de tiques entre áreas.
- Cambio de estado de los tiques a lo largo de su ciclo de vida.
- Registro de historial de acciones por tique.
- Generación de informes filtrados por fecha, tipo, criticidad, área o ejecutivo.
- Control de acceso según perfil de usuario.

### 2.3 Clases de usuario y características
| Usuario | Descripción | Nivel de acceso |
|---|---|---|
| Ejecutivo | Crea, deriva y da seguimiento a los tiques que gestiona | Medio |
| Jefe de mesa | Supervisa todos los tiques, reasigna, genera informes | Alto |

### 2.4 Entorno operativo
Aplicación de escritorio o web interna, uso dentro de la red de la consultora, acceso mediante usuario y contraseña.

### 2.5 Restricciones
- El sistema debe operar con la infraestructura tecnológica actual de la consultora (sin grandes inversiones en hardware).
- Debe permitir el acceso simultáneo de varios ejecutivos.

### 2.6 Supuestos y dependencias
- Se asume que los datos de clientes ya existen o se ingresan manualmente al crear el tique (no hay CRM previo).
- Se asume que las áreas de derivación están predefinidas por la consultora.

---

## 3. Entrevista simulada (toma de requerimientos)

**Entrevistado:** Jefe de Mesa de Ayuda, Consúltenos

**P: ¿Cómo gestionan hoy los tiques de atención?**
R: Todo se lleva en una planilla Excel compartida. Cada ejecutivo anota el caso, pero se pierde el orden y no sabemos en qué estado quedó cada uno sin preguntar directamente.

**P: ¿Qué información necesitan registrar de cada tique?**
R: Nombre del cliente, tipo de problema, qué tan urgente es, una descripción del caso y a qué área se deriva.

**P: ¿Qué estados puede tener un tique?**
R: Puede estar "a resolución" (recién creado o en proceso), "resuelto" cuando se soluciona, o "no aplicable" si no corresponde atenderlo.

**P: ¿Quién puede cerrar un tique?**
R: Cualquier ejecutivo puede cerrar los tiques que tiene asignados, pero yo como jefe de mesa necesito poder ver y reasignar cualquier tique.

**P: ¿Qué informes necesitan?**
R: Principalmente cuántos tiques se abrieron y cerraron por período, por tipo de problema, por criticidad y por ejecutivo, para evaluar carga de trabajo.

**P: ¿Qué pasa si un tique no se resuelve a tiempo?**
R: Por ahora no tenemos alertas automáticas, pero sería ideal tenerlas más adelante.

---

## 4. Requisitos específicos preliminares

### 4.1 Requisitos funcionales
| ID | Descripción |
|---|---|
| RF-01 | El sistema debe permitir crear un tique con datos del cliente, tipo, criticidad, detalle y área asignada. |
| RF-02 | El sistema debe permitir derivar un tique a otra área. |
| RF-03 | El sistema debe permitir cambiar el estado de un tique (A resolución, Resuelto, No aplicable). |
| RF-04 | El sistema debe registrar el historial de acciones de cada tique (quién lo creó, quién lo cerró, observaciones). |
| RF-05 | El sistema debe permitir generar informes filtrados por fecha, tipo, criticidad, área o ejecutivo. |
| RF-06 | El sistema debe controlar el acceso según el perfil del usuario (ejecutivo / jefe de mesa). |
| RF-07 | El sistema debe permitir a un ejecutivo ver y gestionar solo los tiques que tiene asignados, salvo el jefe de mesa que ve todos. |

### 4.2 Requisitos no funcionales
| ID | Descripción |
|---|---|
| RNF-01 | El sistema debe permitir el acceso simultáneo de múltiples ejecutivos sin pérdida de información. |
| RNF-02 | La interfaz debe ser simple e intuitiva, considerando que los ejecutivos vienen de usar planillas Excel. |
| RNF-03 | El sistema debe registrar fecha y hora de cada acción sobre un tique. |
| RNF-04 | El acceso debe requerir autenticación mediante usuario y contraseña. |

---

## 5. Reglas de negocio conocidas
- RN-01: Un tique solo puede estar en un estado a la vez (A resolución, Resuelto o No aplicable).
- RN-02: Solo el jefe de mesa puede reasignar un tique ya derivado a otra área.
- RN-03: Un tique cerrado (Resuelto o No aplicable) no puede volver a editarse, solo consultarse.
- RN-04: Todo tique debe quedar asociado a un ejecutivo responsable.

---

## 6. Análisis inicial de factibilidad

### 6.1 Factibilidad técnica
El proyecto es viable con herramientas de desarrollo estándar (aplicación web o de escritorio con base de datos relacional). No requiere hardware ni licencias especiales adicionales a las que ya maneja la consultora.

### 6.2 Factibilidad de negocio
El sistema reemplaza un proceso manual propenso a errores (pérdida de seguimiento en planillas), por lo que se espera una mejora directa en tiempos de respuesta y en la capacidad de generar informes de gestión, sin requerir una inversión mayor.
