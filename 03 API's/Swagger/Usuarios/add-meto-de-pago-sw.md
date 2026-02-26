### Agregar método de pago - SW

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - para agregar metodo de pago",
    "version": "1.0.0",
    "description": "Permite al usuario guardar un método de pago."
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor principal de la API"
    }
  ],
  "paths": {
    "/addcard": {
      "post": {
        "summary": "Agregar una nueva tarjeta de pago",
        "operationId": "addCard",
        "tags": [
          "Payments"
        ],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddCardRequest"
              },
              "example": {
                "user_id": "{{USER_ID}}",
                "token": "{{USER_TOKEN}}",
                "type": "{{USER_UNIQUE_NUMBER}}",
                "payment_method": "pm_1Jyaj7GuEroovfwJe0BzCQa8"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Tarjeta agregada exitosamente.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddCardSuccessResponse"
                },
                "example": {
                  "success": true,
                  "message": "6",
                  "_id": "619b89875d286307914b0444",
                  "payment_method": "pm_1Jyaj7GuEroovfwJe0BzCQa8",
                  "user_id": "61978529e3a07451a82404a5",
                  "last_four": "4242",
                  "card_type": "visa",
                  "is_default": 1,
                  "type": 10
                }
              }
            }
          },
          "400": {
            "description": "Solicitud inválida o error en la pasarela de pago.",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "success": { "type": "boolean", "example": false },
                    "error_code": { "type": "string", "example": "991" },
                    "message": { "type": "string", "example": "Error processing card" }
                  }
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
        "description": "Cuerpo de la solicitud para agregar una nueva tarjeta.",
        "properties": {
          "user_id": {
            "type": "string",
            "description": "ID del usuario que añade la tarjeta."
          },
          "token": {
            "type": "string",
            "description": "Token de autenticación del usuario."
          },
          "type": {
            "type": "string",
            "description": "Número o código único de la transacción/tipo de usuario."
          },
          "payment_method": {
            "type": "string",
            "description": "Token o ID del método de pago generado por la pasarela de pago (e.g., Stripe Payment Method ID).",
            "example": "pm_1Jyaj7GuEroovfwJe0BzCQa8"
          }
        },
        "required": [
          "user_id",
          "token",
          "type",
          "payment_method"
        ]
      },
      "AddCardSuccessResponse": {
        "type": "object",
        "description": "Respuesta al añadir una tarjeta exitosamente.",
        "properties": {
          "success": {
            "type": "boolean"
          },
          "message": {
            "type": "string",
            "description": "Código o mensaje interno de éxito."
          },
          "_id": {
            "type": "string",
            "description": "ID del documento de la tarjeta recién creada en la base de datos."
          },
          "payment_method": {
            "type": "string",
            "description": "El token de pago utilizado."
          },
          "user_id": {
            "type": "string",
            "description": "ID del usuario asociado a la tarjeta."
          },
          "last_four": {
            "type": "string",
            "description": "Los últimos cuatro dígitos de la tarjeta (devueltos por la pasarela de pago)."
          },
          "card_type": {
            "type": "string",
            "description": "Tipo de tarjeta (e.g., visa)."
          },
          "is_default": {
            "type": "integer",
            "description": "Indica si la tarjeta se ha establecido como predeterminada (1)."
          },
          "type": {
            "type": "integer",
            "description": "Tipo o código interno."
          }
        }
      }
    }
  }
}
```



