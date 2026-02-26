### Eliminar un Conductor de Favoritos

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - Eliminar conducor favorito",
    "version": "1.0.0",
    "description": "API para eliminar un conductor de la lista de favoritos de un usuario."
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
    "/remove_favourite_driver": {
      "post": {
        "summary": "Eliminar conductor de favoritos",
        "description": "Remueve un conductor específico de la lista de favoritos del usuario.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/RemoveFavoriteDriverRequest"
              },
              "example": {
                "user_id": "{{USER_ID}}",
                "token": "{{USER_TOKEN}}",
                "provider_id": "60227d7765b27b2840e6ea25"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Conductor eliminado exitosamente de favoritos.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/RemoveFavoriteDriverResponse"
                },
                "example": {
                  "success": true,
                  "message": "107"
                }
              }
            }
          },
          "400": {
            "description": "Solicitud inválida (ej. falta un campo requerido)."
          },
          "401": {
            "description": "No autorizado (Token inválido)."
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "RemoveFavoriteDriverRequest": {
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
          "provider_id": {
            "type": "string",
            "description": "Identificador único del conductor/proveedor a eliminar."
          }
        },
        "required": [
          "user_id",
          "token",
          "provider_id"
        ]
      },
      "RemoveFavoriteDriverResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación fue exitosa."
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje o estado de éxito (ej. '107')."
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
