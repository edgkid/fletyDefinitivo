
### Crear Promociones

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de creación de Promociones",
    "description": "Endpoint para aplicar códigos de descuento a un viaje específico.",
    "version": "1.0.0"
  },
  "paths": {
    "/apply_promocode": {
      "post": {
        "summary": "Aplicar código promocional",
        "operationId": "applyPromocode",
        "tags": [
          "Promotions"
        ],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/PromoRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Código promocional aplicado con éxito",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/PromoResponse"
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
      "PromoRequest": {
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
          "promocode": {
            "type": "string",
            "example": "FESTIVE"
          }
        },
        "required": [
          "user_id",
          "token",
          "trip_id",
          "promocode"
        ]
      },
      "PromoResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "promo_id": {
            "type": "string",
            "example": "61a23a11f814ee3896fa3e0f"
          },
          "message": {
            "type": "string",
            "example": "37",
            "description": "Código de mensaje o estado de la operación"
          }
        }
      }
    }
  }
}

```
