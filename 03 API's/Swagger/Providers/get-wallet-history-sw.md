### Histórico de Movimientos de Billetera

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Wallet History API",
    "description": "API para consultar el histórico de transacciones y movimientos de la billetera.",
    "version": "1.0.0"
  },
  "paths": {
    "/get_wallet_history": {
      "post": {
        "summary": "Obtener historial de la billetera",
        "description": "Retorna una lista detallada de todos los movimientos realizados en la billetera.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/WalletHistoryRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Listado de movimientos obtenido con éxito",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/WalletHistoryResponse"
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
      "WalletHistoryRequest": {
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
      "WalletHistoryResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "message": { "type": "string", "example": "100" },
          "wallet_history": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/WalletTransaction"
            }
          }
        }
      },
      "WalletTransaction": {
        "type": "object",
        "properties": {
          "_id": { "type": "string", "example": "619662eb7bd38137e5e50f7a" },
          "unique_id": { "type": "integer", "example": 155 },
          "user_type": { "type": "integer", "example": 10 },
          "user_unique_id": { "type": "integer", "example": 34 },
          "user_id": { "type": "string", "example": "61962d683b0daa5338204ce6" },
          "__v": { "type": "integer", "example": 0 },
          "updated_at": { "type": "string", "format": "date-time", "example": "2021-11-18T14:27:55.616Z" },
          "created_at": { "type": "string", "format": "date-time", "example": "2021-11-18T14:27:55.616Z" },
          "total_wallet_amount": { "type": "number", "example": 300 },
          "added_wallet": { "type": "number", "example": 100 },
          "wallet_amount": { "type": "number", "example": 200 },
          "wallet_description": { "type": "string", "example": "Card : 4242" },
          "wallet_comment_id": { "type": "integer", "example": 2 },
          "wallet_status": { "type": "integer", "example": 1 },
          "current_rate": { "type": "number", "example": 1 },
          "to_currency_code": { "type": "string", "example": "INR" },
          "from_currency_code": { "type": "string", "example": "INR" },
          "from_amount": { "type": "number", "example": 100 }
        }
      }
    }
  }
}
```