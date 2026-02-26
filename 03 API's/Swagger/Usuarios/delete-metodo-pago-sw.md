### Elimina un Método de Pago

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - Eliminar metodo de pago",
    "version": "1.0.0",
    "description": "Especificación para la operación de eliminación de un metodo de pago."
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "URL base del servicio"
    }
  ],
  "paths": {
    "/delete_card": {
      "post": {
        "summary": "Eliminar un metodo de pago por ID",
        "description": "Permite a un usuario eliminar un metodo de pago específica de su cuenta.",
        "operationId": "deleteCard",
        "tags": [
          "Tarjetas de Pago"
        ],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/DeleteCardRequest"
              },
              "example": {
                "user_id": "987abc123def456ghi789jkl0mn",
                "token": "a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6",
                "type": 1,
                "card_id": "619b7f53b8dc6178b3d4b306",
                "payment_gateway_type": "stripe"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Tarjeta eliminada exitosamente.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/SuccessResponse"
                },
                "example": {
                  "success": true,
                  "message": "8"
                }
              }
            }
          },
          "400": {
            "description": "Solicitud Inválida o datos faltantes."
          }
          ,
          "401": {
            "description": "Token de autenticación inválido."
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "DeleteCardRequest": {
        "type": "object",
        "properties": {
          "user_id": {
            "type": "string",
            "description": "ID único del usuario.",
            "example": "{{USER_ID}}"
          },
          "token": {
            "type": "string",
            "description": "Token de sesión o autenticación del usuario.",
            "example": "{{USER_TOKEN}}"
          },
          "type": {
            "type": "integer",
            "description": "Número único de identificación (puede ser un tipo de usuario o entidad).",
            "example": "{{USER_UNIQUE_NUMBER}}"
          },
          "card_id": {
            "type": "string",
            "description": "ID de la tarjeta a eliminar.",
            "example": "619b7f53b8dc6178b3d4b306"
          },
          "payment_gateway_type": {
            "type": "string",
            "description": "Tipo de pasarela de pago (ej. stripe, paypal).",
            "example": "{{PAYMENT_GATEWAY_STRIPE}}"
          }
        },
        "required": [
          "user_id",
          "token",
          "type",
          "card_id",
          "payment_gateway_type"
        ]
      },
      "SuccessResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "description": "Indica si la operación fue exitosa.",
            "example": true
          },
          "message": {
            "type": "string",
            "description": "Código o mensaje de respuesta. (Nota: '8' parece ser un código interno, se mantiene según el ejemplo proporcionado).",
            "example": "8"
          }
        },
        "required": [
          "success",
          "message"
        ]
      }
    }
  }
}
```
