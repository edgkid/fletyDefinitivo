
### Notificación de Fallos con Pagos

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Pagos - Stripe Intent Failure",
    "description": "Servicio para notificar y procesar el fallo o la cancelación de un intento de pago.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/fail_stripe_intent_payment": {
      "post": {
        "summary": "Notificar fallo de intención de pago",
        "operationId": "failStripeIntent",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/StripeFailRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Notificación procesada exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/StripeFailResponse"
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
      "StripeFailRequest": {
        "type": "object",
        "required": [
          "trip_id"
        ],
        "properties": {
          "trip_id": {
            "type": "string",
            "description": "Identificador único del viaje relacionado con el pago",
            "example": "{{TRIP_ID}}"
          }
        }
      },
      "StripeFailResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación fue recibida correctamente",
            "example": true
          }
        }
      }
    }
  }
}
```
