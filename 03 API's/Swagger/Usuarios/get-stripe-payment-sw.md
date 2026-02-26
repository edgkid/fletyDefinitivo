### Consulta de Detalles Sobre Pasarela de Pago Stripe

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Payment Intent Detail API",
    "description": "API para enviar detalles alusivo a la pasarela de pagos",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Pagos"
    }
  ],
  "paths": {
    "/send_paystack_required_detail": {
      "post": {
        "summary": "Obtener detalles de intención de pago",
        "description": "Solicita el método de pago  de cliente para procesar pagos mediante Stripe o Paystack.",
        "operationId": "sendPaymentRequiredDetail",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/PaymentRequiredRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Intención de pago generada exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/PaymentRequiredResponse"
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
      "PaymentRequiredRequest": {
        "type": "object",
        "required": [
          "user_id",
          "token",
          "trip_id",
          "type",
          "payment_gateway_type"
        ],
        "properties": {
          "user_id": {
            "type": "string",
            "example": "{{USER_ID}}"
          },
          "token": {
            "type": "string",
            "example": "{{USER_TOKEN}}"
          },
          "trip_id": {
            "type": "string",
            "description": "ID del viaje asociado al pago.",
            "example": "{{TRIP_ID}}"
          },
          "type": {
            "type": "string",
            "description": "Tipo de operación o identificador de flujo.",
            "example": "10"
          },
          "payment_gateway_type": {
            "type": "string",
            "description": "ID de la pasarela de pago (ej. Stripe).",
            "example": "{{PAYMENT_GATEWAY_STRIPE}}"
          }
        }
      },
      "PaymentRequiredResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "payment_method": {
            "type": "string",
            "description": "Identificador del método de pago generado (Stripe PM ID).",
            "example": "pm_1K1AWMHZHvm37V55brdVNQoD"
          },
          "client_secret": {
            "type": "string",
            "description": "Secreto de la intención de pago para confirmar en el lado del cliente.",
            "example": "pi_3K1AWVHZHvm37V551wmpej1V_secret_ZcuWpD7bOSjfvq0Zyzo24qNy2"
          }
        }
      }
    }
  }
}

```
