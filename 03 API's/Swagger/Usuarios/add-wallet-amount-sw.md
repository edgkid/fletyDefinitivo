
### Recargar Wallet

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - para carga saldo a la wallet",
    "version": "1.0.0",
    "description": "API para agregar saldo de la billetera del usuario después de una transacción exitosa."
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
    "/add_wallet_amount": {
      "post": {
        "summary": "Agregar Cantidad a Billetera",
        "description": "Confirma la finalización del pago de una transacción específica y actualiza el saldo de la billetera del usuario.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddWalletAmountRequest"
              },
              "example": {
                "user_id": "{{USER_ID}}",
                "token": "{{USER_TOKEN}}",
                "type": "1",
                "payment_intent_id": "pi_3JxBWxGuEroovfwJ0Pb6FerN",
                "payment_gateway_type": "STRIPE"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Monto agregado exitosamente a la billetera.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddWalletAmountResponse"
                },
                "example": {
                  "success": true,
                  "message": "91",
                  "wallet": 300,
                  "wallet_currency_code": "INR"
                }
              }
            }
          },
          "401": {
            "description": "Token de autenticación inválido."
          },
          "400": {
            "description": "Error en la validación del intento de pago (payment_intent_id)."
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "AddWalletAmountRequest": {
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
          "type": {
            "type": "string",
            "description": "Tipo de transacción o identificador único de la operación de pago."
          },
          "payment_intent_id": {
            "type": "string",
            "description": "ID de la intención de pago generada por la pasarela de pago (ej. Stripe)."
          },
          "payment_gateway_type": {
            "type": "string",
            "description": "Tipo de pasarela de pago utilizada (ej. 'STRIPE')."
          }
        },
        "required": [
          "user_id",
          "token",
          "type",
          "payment_intent_id",
          "payment_gateway_type"
        ]
      },
      "AddWalletAmountResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación de recarga fue exitosa."
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje o estado de éxito (ej. '91')."
          },
          "wallet": {
            "type": "number",
            "format": "float",
            "description": "Nuevo saldo total de la billetera del usuario."
          },
          "wallet_currency_code": {
            "type": "string",
            "description": "Código de la moneda del saldo de la billetera (ej. 'INR')."
          }
        },
        "required": [
          "success",
          "message",
          "wallet",
          "wallet_currency_code"
        ]
      }
    }
  }
}

```
