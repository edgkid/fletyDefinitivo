### Recarga la Billetera

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Wallet API",
    "description": "API para la gestión de fondos permite la recarga de la billetera",
    "version": "1.0.0"
  },
  "paths": {
    "/add_wallet_amount": {
      "post": {
        "summary": "Agregar saldo a la billetera",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddWalletRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Saldo agregado exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddWalletResponse"
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
      "AddWalletRequest": {
        "type": "object",
        "required": [
          "user_id",
          "token",
          "type",
          "payment_intent_id",
          "payment_gateway_type"
        ],
        "properties": {
          "user_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}"
          },
          "token": {
            "type": "string",
            "example": "{{PROVIDER_TOKEN}}"
          },
          "type": {
            "type": "string",
            "example": "{{PROVIDER_UNIQUE_NUMBER}}"
          },
          "payment_intent_id": {
            "type": "string",
            "example": "pi_3JxBWxGuEroovfwJ0Pb6FerN"
          },
          "payment_gateway_type": {
            "type": "string",
            "example": "{{PAYMENT_GATEWAY_STRIPE}}"
          }
        }
      },
      "AddWalletResponse": {
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
            "example": 300
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
