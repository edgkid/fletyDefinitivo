### Actualización de Proveedor

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Proveedores - Actualización de Perfil",
    "description": "Servicio para actualizar categoría de un proveedor en el sistema.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/providerupdatetype": {
      "post": {
        "summary": "Actualizar tipo de proveedor",
        "operationId": "updateProviderType",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/UpdateTypeRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Actualización procesada exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/UpdateTypeResponse"
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
      "UpdateTypeRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "typeid",
          "token"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "description": "ID único del proveedor (MongoDB ObjectID)",
            "example": "619f731fcca616635ef3554c"
          },
          "typeid": {
            "type": "string",
            "description": "ID de la nueva categoría o tipo a asignar",
            "example": "609cf39fea83e15c92e3fc44"
          },
          "token": {
            "type": "string",
            "description": "Token de sesión activo",
            "example": "jyJjjdsQLqSDbIbXerfzfihwWK5VmG0A"
          }
        }
      },
      "UpdateTypeResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje de éxito",
            "example": "59"
          }
        }
      }
    }
  }
}
```
