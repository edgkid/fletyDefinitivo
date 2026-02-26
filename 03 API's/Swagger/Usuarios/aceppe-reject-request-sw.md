### Aceptar o Rechazar Viaje

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - aceptación o rechazo de solicitudes",
    "version": "1.0.0",
    "description": "API para gestionar la aceptación o rechazo de solicitudes de un usuario a una corporación."
  },
  "paths": {
    "/corporate/request/response": {
      "post": {
        "summary": "Responder a una solicitud de unión corporativa",
        "description": "Permite a un usuario aceptar o rechazar una solicitud de unión a una corporación específica.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "user_id": {
                    "type": "string",
                    "description": "ID del usuario que responde a la solicitud."
                  },
                  "token": {
                    "type": "string",
                    "description": "Token único de sesión o autenticación del usuario."
                  },
                  "is_accepted": {
                    "type": "boolean",
                    "description": "Indica si el usuario aceptó (true) o rechazó (false) la solicitud."
                  },
                  "corporate_id": {
                    "type": "string",
                    "description": "ID de la corporación a la que se refiere la solicitud."
                  }
                },
                "required": [
                  "user_id",
                  "token",
                  "is_accepted",
                  "corporate_id"
                ],
                "example": {
                  "user_id": "{{USER_ID}}",
                  "token": "{{USER_TOKEN}}",
                  "is_accepted": true,
                  "corporate_id": "619cd3600b2b21777c6104be"
                }
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Respuesta exitosa, la solicitud ha sido procesada.",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "success": {
                      "type": "boolean",
                      "description": "Indica si la operación fue exitosa."
                    },
                    "message": {
                      "type": "string",
                      "description": "Código o mensaje de respuesta. (Ej: '103')"
                    }
                  },
                  "example": {
                    "success": true,
                    "message": "103"
                  }
                }
              }
            }
          },
          "400": {
            "description": "Solicitud inválida (ej. token, ID o formato incorrecto)."
          },
          "401": {
            "description": "No autorizado (ej. token expirado o no válido)."
          }
        }
      }
    }
  }
}
```

