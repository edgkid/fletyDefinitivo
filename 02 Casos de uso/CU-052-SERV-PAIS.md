## Caso de Uso: CU-052-SERV-PAÍS - País

Este caso de uso describe la funcionalidad que permite al administrador gestionar las regiones geográficas donde opera la plataforma, estableciendo los parámetros base como moneda, prefijos telefónicos y disponibilidad del servicio.

### 📋 Información General

| Sección | Descripción |
| :--- | :--- |
| **ID** | CU-052-SERV-PAÍS |
| **Caso de Uso** | País |
| **Actor Principal** | Usuario |
| **Actor Secundario** | Software |
| **Objetivo** | Administrar los países donde la plataforma opera, configurando la moneda, métodos de pago y códigos telefónicos. |
| **Prioridad** | Alta |

---

### 🛠️ Precondiciones del Sistema
* El usuario inicia sesión de forma exitosa (**CU-001-ADM / CU-001-CLI**).
* El usuario cuenta con el rol y los permisos pertinentes.

---

### 🔄 Flujo del Sistema

| Actor Principal (Usuario)                                                                                                                                                                  | Actor Secundario (Sistema)                                                                          |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------- |
|                                                                                                                                                                                            | 1) El sistema presenta una cuadrícula de tarjetas que representan los países activos o registrados. |
| 2) El usuario visualiza de forma rápida: **Bandera**, **Nombre**, **Moneda** (ej. ₹, Bs), **Código de teléfono** (ej. +58) y **Estado del Negocio** (ON/OFF) y campo de pago al conductor. |                                                                                                     |
| 3) El usuario puede filtrar la información mostrada.                                                                                                                                       |                                                                                                     |
| **Fin**                                                                                                                                                                                    |                                                                                                     |

---

### 🔀 Flujo Alternativo del Sistema

| Acción del Usuario | Reacción del Sistema |
| :--- | :--- |
| El usuario desea editar un país registrado. | El sistema redirige a **CU-053-SERV-PAED**. |
| El usuario desea agregar un nuevo país. | El sistema redirige a **CU-054-SERV-NWPA**. |

---

### ✅ Post-Condiciones

| Escenario | Resultado Esperado |
| :--- | :--- |
| **Éxito** | La configuración regional se actualiza, afectando la moneda que ven los usuarios y los formatos de número telefónico en los registros de dicha región. |
| **Fallo** | Si ocurre un error de red, el sistema mantiene la configuración previa y notifica al usuario que los cambios no fueron persistidos. |

---

### 🔗 Casos de Uso Relacionados
* [CU-053-SERV-PAED](02%20Casos%20de%20uso/CU-053-SERV-PAED.md)
* [CU-054-SERV-NWPA](02%20Casos%20de%20uso/CU-054-SERV-NWPA.md)