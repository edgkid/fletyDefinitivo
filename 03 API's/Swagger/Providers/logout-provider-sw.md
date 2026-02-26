### Cierre de Sesión

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider API - logout",
    "description": "Servcio para el cierre de sesión de un proveedor",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor principal"
    }
  ],
  "paths": {
    "/providerlogout": {
      "post": {
        "summary": "Provider Logout",
        "description": "Endpoint para cerrar la sesión de un proveedor utilizando su ID y token.",
        "operationId": "providerLogout",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/LogoutRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Logout exitoso",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/LogoutResponse"
                }
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "LogoutRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}",
            "description": "Identificador único del proveedor"
          },
          "token": {
            "type": "string",
            "example": "{{PROVIDER_TOKEN}}",
            "description": "Token de autenticación del proveedor"
          }
        }
      },
      "LogoutResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "20",
            "description": "Código de mensaje de respuesta"
          }
        }
      }
    }
  }
}


```
