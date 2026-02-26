### Consulta Métodos de Pago Disponible

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Payment Methods API",
    "description": "API para obtener el listado de métodos de pago registrados.",
    "version": "1.0.0"
  },
  "paths": {
    "/cards": {
      "post": {
        "summary": "Obtener métodos de pago ",
        "description": "",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/CardsRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Listado de tarjetas y pasarelas obtenido con éxito",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/CardsResponse"
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
      "CardsRequest": {
        "type": "object",
        "required": ["user_id", "token", "type"],
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
          }
        }
      },
      "CardsResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "message": { "type": "string", "example": "7" },
          "wallet": { "type": "number", "example": 100 },
          "wallet_currency_code": { "type": "string", "example": "INR" },
          "is_use_wallet": { "type": "integer", "example": 1 },
          "payment_gateway": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "id": { "type": "integer", "example": 10 },
                "name": { "type": "string", "example": "" },
                "is_add_card": { "type": "boolean", "example": true }
              }
            }
          },
          "payment_gateway_type": { "type": "integer", "example": 10 },
          "card": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/CardDetail"
            }
          }
        }
      },
      "CardDetail": {
        "type": "object",
        "properties": {
          "_id": { "type": "string", "example": "619b7f53b8dc6178b3d4b306" },
          "user_id": { "type": "string", "example": "61978529e3a07451a82404a5" },
          "type": { "type": "integer", "example": 10 },
          "__v": { "type": "integer", "example": 0 },
          "updated_at": { "type": "string", "format": "date-time", "example": "2021-11-22T11:30:27.892Z" },
          "created_at": { "type": "string", "format": "date-time", "example": "2021-11-22T11:30:27.892Z" },
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
