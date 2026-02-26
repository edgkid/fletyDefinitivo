
### Agregar Conductor a Favoritos

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "PAI - Agregar a favoritos",
    "version": "1.0.0",
    "description": "API para agregar un conductor a la lista de favoritos de un usuario."
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
    "/add_favourite_driver": {
      "post": {
        "summary": "Agregar conductor a favoritos",
        "description": "Asigna un conductor específico al usuario como favorito.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddFavoriteDriverRequest"
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
            "description": "Conductor agregado exitosamente a favoritos.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddFavoriteDriverResponse"
                },
                "example": {
                  "success": true,
                  "message": "106"
                }
              }
            }
          },
          "400": {
            "description": "Solicitud inválida (ej. falta un campo requerido)."
          },
          "401": {
            "description": "No autorizado (Token inválido)."
          },
          "404": {
            "description": "Conductor o usuario no encontrado."
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "AddFavoriteDriverRequest": {
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
            "description": "Identificador único del conductor/proveedor a agregar."
          }
        },
        "required": [
          "user_id",
          "token",
          "provider_id"
        ]
      },
      "AddFavoriteDriverResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación fue exitosa."
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje o estado de éxito (ej. '106')."
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
