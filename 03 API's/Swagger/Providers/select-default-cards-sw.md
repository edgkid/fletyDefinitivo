### Selección de Método de Pago por Defecto

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Card Selection API",
    "description": "API para seleccionar una tarjeta específica como método de pago predeterminado.",
    "version": "1.0.0"
  },
  "paths": {
    "/card_selection": {
      "post": {
        "summary": "Seleccionar tarjeta predeterminada",
        "description": "Establece una tarjeta registrada como la opción principal para futuras transacciones del usuario o proveedor.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/CardSelectionRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Tarjeta seleccionada correctamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/CardSelectionResponse"
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
      "CardSelectionRequest": {
        "type": "object",
        "required": [
          "user_id",
          "token",
          "type",
          "card_id",
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
          "card_id": {
            "type": "string",
            "example": "619b9e9b0fb87b2eb1603faf"
          },
          "payment_gateway_type": {
            "type": "string",
            "example": "{{PAYMENT_GATEWAY_STRIPE}}"
          }
        }
      },
      "CardSelectionResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "card": {
            "$ref": "#/components/schemas/CardDetail"
          }
        }
      },
      "CardDetail": {
        "type": "object",
        "properties": {
          "_id": { "type": "string", "example": "619b9e9b0fb87b2eb1603faf" },
          "user_id": { "type": "string", "example": "61979073da10546535a80fc1" },
          "type": { "type": "integer", "example": 11 },
          "__v": { "type": "integer", "example": 0 },
          "updated_at": { "type": "string", "format": "date-time", "example": "2021-11-22T13:43:55.754Z" },
          "created_at": { "type": "string", "format": "date-time", "example": "2021-11-22T13:43:55.754Z" },
          "payment_gateway_type": { "type": "integer", "example": 10 },
          "is_default": { "type": "integer", "example": 1 },
          "customer_id": { "type": "string", "example": "" },
          "last_four": { "type": "string", "example": "4242" },
          "card_type": { "type": "string", "example": "visa" },
          "payment_method": { "type": "string", "example": "pm_1Jyaj7GuEroovfwJe0BzCQa8" }
        }
      }
    }
  }
}


```
