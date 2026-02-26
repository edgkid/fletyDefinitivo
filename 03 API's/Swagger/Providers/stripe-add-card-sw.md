### Añadir Stripe Como Método de Pago

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Add Card API",
    "description": "API para el registro y vinculación de un metodo de pago a travez de stripe",
    "version": "1.0.0"
  },
  "paths": {
    "/addcard": {
      "post": {
        "summary": "Registrar nueva tarjeta",
        "description": "Vincula un método de pago procesado por el Gateway a la cuenta del usuario.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddCardRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Tarjeta registrada exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddCardResponse"
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
      "AddCardRequest": {
        "type": "object",
        "required": ["user_id", "token", "type", "payment_method"],
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
          "payment_method": {
            "type": "string",
            "description": "ID del método de pago generado por el proveedor de pagos (ej. Stripe).",
            "example": "pm_1Jyaj7GuEroovfwJe0BzCQa8"
          }
        }
      },
      "AddCardResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "6"
          },
          "_id": {
            "type": "string",
            "example": "619b9e9b0fb87b2eb1603faf"
          },
          "payment_method": {
            "type": "string",
            "example": "pm_1Jyaj7GuEroovfwJe0BzCQa8"
          },
          "user_id": {
            "type": "string",
            "example": "61979073da10546535a80fc1"
          },
          "last_four": {
            "type": "string",
            "example": "4242"
          },
          "card_type": {
            "type": "string",
            "example": "visa"
          },
          "is_default": {
            "type": "integer",
            "example": 1
          },
          "type": {
            "type": "integer",
            "example": 11
          }
        }
      }
    }
  }
}
```
