### Eliminar un Código Promocional

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Gestión promociones - eliminar",
    "description": "Endpoint para eliminar un código promocional aplicado previamente a un viaje.",
    "version": "1.0.0"
  },
  "paths": {
    "/remove_promocode": {
      "post": {
        "summary": "Remover código promocional",
        "operationId": "removePromocode",
        "tags": ["Promotions"],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/RemovePromoRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Código promocional removido exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/RemovePromoResponse"
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
      "RemovePromoRequest": {
        "type": "object",
        "properties": {
          "user_id": {
            "type": "string",
            "example": "61a239b..."
          },
          "token": {
            "type": "string",
            "example": "eyJhbG..."
          },
          "trip_id": {
            "type": "string",
            "example": "619e48cca3a3924e076c558f"
          },
          "promo_id": {
            "type": "string",
            "example": "61a23a11f814ee3896fa3e0f"
          }
        },
        "required": ["user_id", "token", "trip_id", "promo_id"]
      },
      "RemovePromoResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "105",
            "description": "Código de éxito para la eliminación del promo"
          }
        }
      }
    }
  }
}


```
