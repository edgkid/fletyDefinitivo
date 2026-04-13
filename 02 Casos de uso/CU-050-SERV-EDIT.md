# ## Caso de Uso: CU-050-SERV-EDIT - Editar Tipo de Servicios

Este caso de uso describe el proceso para modificar la configuración operativa, las capacidades técnicas y los recursos visuales de un tipo de vehículo específico dentro de la plataforma.

### 📋 Información General

| Sección | Descripción |
| :--- | :--- |
| **ID** | CU-050-SERV-EDIT |
| **Caso de Uso** | Edit Tipo de Servicios |
| **Actor Principal** | Usuario |
| **Actor Secundario** | Software |
| **Objetivo** | Permite editar la información de un tipo de servicio y configurar los parámetros operativos, capacidades y recursos gráficos de un tipo de vehículo específico. |
| **Prioridad** | Alta |

---

### 🛠️ Precondiciones del Sistema
* El usuario inicia sesión de forma exitosa (**CU-001-ADM / CU-001-CLI**).
* El usuario cuenta con el rol y los permisos pertinentes.
* El usuario seleccionó la opción de editar servicio desde **CU-049-SERV-TIPO**.

---

### 🔄 Flujo del Sistema

| Actor Principal (Usuario)                                                                                                                                      | Actor Secundario (Sistema)                                                                                                                           |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                                                                                                                                                | 1) El sistema despliega el formulario con los campos precargados: Nombre de tipo 1, Nombre de tipo 2 (rango de capacidad), y el número de secuencia. |
| 2) El usuario define si el servicio está activo (**Negocio ON/OFF**).                                                                                          |                                                                                                                                                      |
| 3) El usuario activa/desactiva mediante interruptores las propiedades: ¿Tiene Capacidad?, ¿Tiene tipo de camión?, ¿Tiene servicios?, ¿Tiene especificaciones?. |                                                                                                                                                      |
| 4) **Asignación de Parámetros**: Si están activos, el usuario selecciona de listas desplegables los "Servicios" relacionados y el "Modelo de Camión".          |                                                                                                                                                      |
| 5) El usuario puede marcar el vehículo como "Selección por defecto" mediante un interruptor.                                                                   |                                                                                                                                                      |
| 6) El usuario carga o cambia las imágenes: **Fotografía representativa**, **Imagen de marcador de mapa** e **Imagen de pin del panel**.                        |                                                                                                                                                      |
| 7)EL usuario puede indicar medidas, paletas y capacidades.                                                                                                     |                                                                                                                                                      |
| 8) Presiona guardar.                                                                                                                                           | 9) El sistema deja persistencia de los datos y redirige a **CU-049-SERV-TIPO**.                                                                      |
| **Fin**                                                                                                                                                        |                                                                                                                                                      |

---

### 🖼️ Recursos Gráficos Gestionados
* **Tipo de imagen**: Fotografía representativa del vehículo para la interfaz.
* **Imagen de marcador de mapa**: Icono que visualizará el cliente en su aplicación.
* **Imagen de pin del mapa del panel**: Icono utilizado para el seguimiento en el panel administrativo.

---

### ✅ Post-Condiciones

| Escenario | Resultado Esperado |
| :--- | :--- |
| **Éxito** | Los cambios se almacenan en la base de datos y se actualizan los iconos en el mapa en tiempo real para todos los usuarios. |
| **Fallo** | El sistema muestra una notificación de error; no se modifica la configuración previa y el administrador permanece en la pantalla de edición. |

---

### 🔗 Casos de Uso Relacionados
* [Tipo de Servicios (CU-049)](02%20Casos%20de%20uso/CU-049-Servicio.md)