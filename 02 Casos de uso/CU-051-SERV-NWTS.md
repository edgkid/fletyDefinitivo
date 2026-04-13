## Caso de Uso: CU-051-SERV-NWTS - Nuevo Tipo de Servicios

Este caso de uso describe el proceso para registrar una nueva categoría de vehículo en el catálogo del sistema, permitiendo expandir la oferta de servicios disponibles para los clientes.

### 📋 Información General

| Sección | Descripción |
| :--- | :--- |
| **ID** | CU-051-SERV-NWTS |
| **Caso de Uso** | Nuevo Tipo de Servicios |
| **Actor Principal** | Usuario |
| **Actor Secundario** | Software |
| **Objetivo** | Permite registrar una nueva categoría de vehículo en el catálogo del sistema para expandir la oferta de servicios. |
| **Prioridad** | Alta |

---

### 🛠️ Precondiciones del Sistema
* El usuario inicia sesión de forma exitosa (**CU-001-ADM / CU-001-CLI**).
* El usuario cuenta con el rol y los permisos pertinentes.
* El usuario seleccionó la opción de agregar servicio desde **CU-049-SERV-TIPO**.

---

### 🔄 Flujo del Sistema

| Actor Principal (Usuario)                                                                                                                                                                  | Actor Secundario (Sistema)                                                                                                  |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------- |
|                                                                                                                                                                                            | 1) El sistema presenta un formulario en blanco con valores por defecto (ej. Negocio en "ON" y switches en estado inactivo). |
| 2) El usuario ingresa el "Nombre de tipo 1" (Nombre comercial) y el "Nombre de tipo 2" (Descripción secundaria o capacidad).                                                               |                                                                                                                             |
| 3) Se asigna un "Número de secuencia" para determinar la posición del nuevo vehículo en la interfaz del cliente.                                                                           |                                                                                                                             |
| 4) El usuario activa los interruptores necesarios según las características del vehículo: **¿Tiene Capacidad?**, **¿Tiene Modelo?**, **¿Tiene servicios?** y **¿Tiene especificaciones?**. |                                                                                                                             |
| 5) El usuario carga los tres archivos de imagen obligatorios.                                                                                                                              |                                                                                                                             |
| 6)Indica información de capacidad, servicio y modelos                                                                                                                                      |                                                                                                                             |
| 7) El usuario presiona el botón "Enviar".                                                                                                                                                  | 8) El sistema deja persistencia de los datos y redirige a **CU-049-SERV-TIPO**.                                             |
| **Fin**                                                                                                                                                                                    |                                                                                                                             |
|                                                                                                                                                                                            |                                                                                                                             |

---

### ⚙️ Características Configurables
* **¿Tiene Capacidad?**: Habilita el selector de volumen o peso.
* **¿Tiene Modelo?**: Habilita el selector de marca y modelo.
* **¿Tiene servicios?**: Habilita la asociación con servicios existentes (ej. Cisterna de agua).
* **¿Tiene especificaciones?**: Habilita botones para medidas técnicas y paletas.

---

### ✅ Post-Condiciones

| Escenario | Resultado Esperado |
| :--- | :--- |
| **Éxito** | El nuevo tipo de servicio se añade a la base de datos, se genera su "Card" en la vista principal y queda disponible para su uso en la plataforma. |
| **Fallo** | El sistema no crea el registro, informando al usuario sobre la falla técnica o el dato faltante. |

---

### 🔗 Casos de Uso Relacionados
* [Tipo de Servicios (CU-049)](02%20Casos%20de%20uso/CU-049-Servicio.md)