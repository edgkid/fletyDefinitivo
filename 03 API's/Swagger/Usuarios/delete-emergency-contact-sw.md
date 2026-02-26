### Eliminar Contacto de Emergencia

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - eliminar contacto de emergencia",
    "version": "1.0.0",
    "description": "API para eliminar un contacto de emergencia de un usuario."
  },
  "servers": [
    {
      "url": "{URL}",
      "variables": {
        "URL": {
          "default": "https://api.ejemplo.com",
          "description": "URL base de la API."
        }
      }
    }
  ],
  "paths": {
    "/delete_emergency_contact": {
      "post": {
        "summary": "Eliminar Contacto de Emergencia",
        "description": "Elimina un contacto de emergencia específico utilizando su identificador.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/DeleteEmergencyContactRequest"
              },
              "example": {
                "user_id": "{{USER_ID}}",
                "token": "{{USER_TOKEN}}",
                "emergency_contact_detail_id": "61965bc435a1c02ca00d3483"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "El contacto fue eliminado exitosamente.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/DeleteEmergencyContactResponse"
                },
                "example": {
                  "success": true,
                  "message": "69"
                }
              }
            }
          },
          "401": {
            "description": "Token de autenticación inválido."
          },
          "404": {
            "description": "Contacto de emergencia no encontrado para el ID proporcionado."
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "DeleteEmergencyContactRequest": {
        "type": "object",
        "properties": {
          "user_id": {
            "type": "string",
            "description": "Identificador único del usuario."
          },
          "token": {
            "type": "string",
            "description": "Token de autenticación del usuario."
          },
          "emergency_contact_detail_id": {
            "type": "string",
            "description": "ID del contacto de emergencia a eliminar."
          }
        },
        "required": [
          "user_id",
          "token",
          "emergency_contact_detail_id"
        ]
      },
      "DeleteEmergencyContactResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación de eliminación fue exitosa."
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje o estado de éxito (ej. '69')."
          }
        },
        "required": [
          "success",
          "message"
        ]
      }
    }
  }
}
```
