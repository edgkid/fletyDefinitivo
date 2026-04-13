## Caso de Uso: CU-053-SERV-PAED - Editar País

Este caso de uso describe el proceso de modificación de los parámetros regionales de un país, permitiendo al administrador ajustar la economía del sistema (moneda), la logística de pagos (pasarelas y transferencias) y las estrategias de crecimiento (referidos).

### 📋 Información General

| Sección | Descripción |
| :--- | :--- |
| **ID** | CU-053-SERV-PAED |
| **Caso de Uso** | Editar país |
| **Actor Principal** | Usuario |
| **Actor Secundario** | Software |
| **Objetivo** | Permite modificar los ajustes básicos, métodos de pago, sistemas de referidos y pasarelas de pago para un país operativo. |
| **Prioridad** | Alta |

---

### 🛠️ Precondiciones del Sistema
* El usuario inicia sesión de forma exitosa (**CU-001-ADM / CU-001-CLI**).
* El usuario cuenta con el rol y los permisos pertinentes.
* El usuario seleccionó la opción de editar país desde **CU-052-SERV-PAÍS**.

---

### 🔄 Flujo del Sistema

| Actor Principal (Usuario)                                                                                                                                      | Actor Secundario (Sistema)                                                      |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
|                                                                                                                                                                | 1) El sistema carga la información de los parámetros de país seleccionados.     |
| 2) El usuario modifica el estado de operación (ON/OFF), nombre, código de moneda (ej. INR), símbolo (₹) y código de teléfono (+91).                            |                                                                                 |
| 3) El usuario selecciona el método de pago (**Banco** o **Efectivo**) al conductor. Si es Banco, define el día y zona horaria para transferencias automáticas. |                                                                                 |
| 4) El usuario configura el **Sistema de Referidos** de usuarios y conductores: activa interruptores y define montos (amigo, propio) y límite de usos.          |                                                                                 |
| 5) El usuario elige la **Pasarela de Pago** activa (Stripe, Paystack o Payu).                                                                                  |                                                                                 |
| 6) El usuario presiona el botón "Enviar".                                                                                                                      | 7) El sistema deja persistencia de los datos y redirige a **CU-052-SERV-PAÍS**. |
| **Fin**                                                                                                                                                        |                                                                                 |

---

### ⚙️ Configuraciones Críticas
* **Gestión Financiera**: Selección entre pagos manuales o automatización bancaria programada.
* **Estrategia de Referidos**: Control granular sobre bonificaciones por invitación.
* **Integración de Pagos**: Selección de la API proveedora según la región geográfica.

---

### ✅ Post-Condiciones

| Escenario | Resultado Esperado |
| :--- | :--- |
| **Éxito** | Los nuevos parámetros de moneda, bonos y pasarelas se actualizan inmediatamente para todos los usuarios y conductores que operan en dicho país. |
| **Fallo** | El sistema muestra una notificación de error; los ajustes regionales previos permanecen intactos para no interrumpir la operación. |

---

### 🔗 Casos de Uso Relacionados
* [CU-052-SERV-PAÍS](02%20Casos%20de%20uso/CU-052-SERV-PAIS.md)