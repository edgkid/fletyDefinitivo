
### Cancelar Viajes

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Proveedores - Cancelación de Viajes",
    "description": "API para cancelar un viaje.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de desarrollo/pruebas"
    }
  ],
  "paths": {
    "/tripcancelbyprovider": {
      "post": {
        "summary": "Cancelar viaje por proveedor",
        "operationId": "cancelTripByProvider",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/CancelTripRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Operación procesada (puede ser éxito o error de negocio)",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/CancelTripResponse"
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
      "CancelTripRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token",
          "trip_id",
          "cancel_reason"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}"
          },
          "token": {
            "type": "string",
            "example": "{{PROVIDER_TOKEN}}"
          },
          "trip_id": {
            "type": "string",
            "example": "{{TRIP_ID}}"
          },
          "cancel_reason": {
            "type": "string",
            "example": "My client and I couldn't connect."
          }
        }
      },
      "CancelTripResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "57"
          },
          "is_trip_cancelled_by_provider": {
            "type": "integer",
            "example": 1
          }
        }
      }
    }
  }
}
```
