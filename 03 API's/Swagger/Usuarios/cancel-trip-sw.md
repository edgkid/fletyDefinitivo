### Cancelar Viaje
```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Cancel Trip API",
    "description": "API para cancelar un viaje en curso o programado por parte del usuario.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor principal"
    }
  ],
  "paths": {
    "/canceltrip": {
      "post": {
        "summary": "Cancelar un viaje",
        "description": "Permite a un usuario cancelar un viaje proporcionando un motivo específico.",
        "operationId": "cancelTrip",
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
            "description": "Operación de cancelación procesada",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/CancelTripResponse"
                }
              }
            }
          },
          "401": {
            "description": "Token de usuario inválido o sesión expirada"
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
          "user_id",
          "token",
          "trip_id",
          "cancel_reason"
        ],
        "properties": {
          "user_id": {
            "type": "string",
            "description": "ID único del usuario",
            "example": "61978529e3a07451a82404a5"
          },
          "token": {
            "type": "string",
            "description": "Token de autenticación del usuario",
            "example": "USER_TOKEN_HERE"
          },
          "trip_id": {
            "type": "string",
            "description": "ID del viaje que se desea cancelar",
            "example": "619f99ecc68548396ff542a4"
          },
          "cancel_reason": {
            "type": "string",
            "description": "Motivo por el cual se cancela el servicio",
            "example": "My driver and I couldn't connect."
          }
        }
      },
      "CancelTripResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación fue exitosa",
            "example": true
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje de respuesta",
            "example": "11"
          }
        }
      }
    }
  }
}

```
