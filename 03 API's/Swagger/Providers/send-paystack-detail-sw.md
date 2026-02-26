

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Pagos - Paystack Verification",
    "description": "Servicio para enviar detalles adicionales  para procesar transacciones a través de la pasarela Paystack.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/send_paystack_required_detail": {
      "post": {
        "summary": "Validar detalles de pago Paystack",
        "operationId": "verifyPaystackPayment",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/PaystackDetailRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Transacción verificada y procesada",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/PaystackDetailResponse"
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
      "PaystackDetailRequest": {
        "type": "object",
        "required": [
          "amount",
          "user_id",
          "token",
          "reference"
        ],
        "properties": {
          "amount": {
            "type": "number",
            "example": 105
          },
          "otp": {
            "type": "string",
            "example": "123456"
          },
          "reference": {
            "type": "string",
            "example": "msozhe6jw2e7n0r"
          },
          "user_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}"
          },
          "payment_gateway_type": {
            "type": "integer",
            "example": 11
          },
          "token": {
            "type": "string",
            "example": "{{PROVIDER_TOKEN}}"
          },
          "pin": {
            "type": "string",
            "example": "1234"
          },
          "type": {
            "type": "integer",
            "example": 11
          },
          "required_param": {
            "type": "string",
            "example": "send_otp"
          },
          "phone": {
            "type": "string",
            "example": ""
          }
        }
      },
      "PaystackDetailResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "91"
          },
          "wallet": {
            "type": "number",
            "format": "float",
            "example": 106
          },
          "wallet_currency_code": {
            "type": "string",
            "example": "INR"
          }
        }
      }
    }
  }
}


```
