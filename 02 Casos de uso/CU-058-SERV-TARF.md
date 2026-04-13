## Caso de Uso: CU-058-SERV-TARF - Tarifas

Este caso de uso describe la funcionalidad que permite al administrador supervisar, organizar y gestionar la estructura de costos de los servicios, permitiendo un control detallado sobre los precios aplicados según la región y el tipo de transporte.

### 📋 Información General

| Sección | Descripción |
| :--- | :--- |
| **ID** | CU-058-SERV-TARF |
| **Caso de Uso** | Tarifas |
| **Actor Principal** | Usuario |
| **Actor Secundario** | Software |
| **Objetivo** | Permitir la visualización, creación y gestión de todas las tarifas existentes en los parámetros del sistema. |
| **Prioridad** | Alta |

---

### 🛠️ Precondiciones del Sistema
* El usuario inicia sesión de forma exitosa (**CU-001-ADM / CU-001-CLI**).
* El usuario cuenta con el rol y los permisos pertinentes.

---

### 🔄 Flujo del Sistema

| Actor Principal (Usuario)                                         | Actor Secundario (Sistema)                                                                                                                                                                                |
| :---------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                                                   | 1) El sistema consulta y despliega el listado de tarifas: País, países de negocio,  Ciudad, ciudades de negocio,  Tipo de Precio, Tipo, tipo de negocio, tipo de Vehículo, estatus de negocio y opciones. |
| 2) El usuario puede clasificar la lista por Ciudad.               |                                                                                                                                                                                                           |
| 3) El usuario puede buscar una tarifa específica.                 |                                                                                                                                                                                                           |
| 4) El usuario puede filtrar los registros por un rango de fechas. |                                                                                                                                                                                                           |
| 5) El usuario selecciona el botón "Exportar".                     | 6) El sistema construye y descarga el documento (Excel/CSV) con la información visible.                                                                                                                   |
| **Fin**                                                           |                                                                                                                                                                                                           |

---

### 🔀 Flujo Alternativo del Sistema

| Acción del Usuario | Reacción del Sistema |
| :--- | :--- |
| El usuario desea editar una tarifa específica. | El sistema redirige a **CU-059-SERV-TAED**. |
| El usuario desea agregar una nueva tarifa. | El sistema redirige a **CU-060-SERV-NWTA**. |

---

### ✅ Post-Condiciones

| Escenario | Resultado Esperado |
| :--- | :--- |
| **Éxito (Sincronización)** | Cualquier cambio realizado a través de las opciones de edición se refleja inmediatamente en el módulo de facturación de servicios. |
| **Éxito (Visualización)** | Se mantiene la lista actualizada según los filtros aplicados. |
| **Fallo** | El sistema no logra recuperar la data y muestra un mensaje de error de conexión. |

---

### 🔗 Casos de Uso Relacionados
* [CU-059-SERV-TAED](02%20Casos%20de%20uso/CU-059-SERV-TAED.md)
* [CU-060-SERV-NWTA](02%20Casos%20de%20uso/CU-060-SERV-NWTA.md)