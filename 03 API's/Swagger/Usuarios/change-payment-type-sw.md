### Cambiar Método de Pago

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Change Payment Type API",
    "description": "API que permite al usuario cambiar el método de pago.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Producción"
    }
  ],
  "paths": {
    "/userchangepaymenttype": {
      "post": {
        "summary": "Cambiar el tipo de pago del viaje",
        "description": "Actualiza el método de pago asociado a un trip_id activo.",
        "operationId": "changePaymentType",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/ChangePaymentRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Cambio de pago exitoso",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/StandardResponse"
                }
              }
            }
          },
          "400": {
            "description": "Petición incorrecta o datos faltantes"
          },
          "401": {
            "description": "Sesión expirada o token inválido"
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "ChangePaymentRequest": {
        "type": "object",
        "required": [
          "user_id",
          "token",
          "trip_id",
          "payment_type"
        ],
        "properties": {
          "user_id": {
            "type": "string",
            "example": "61978529e3a07451a82404a5"
          },
          "token": {
            "type": "string",
            "example": "61978529e3a07451a82404a5_61978529e3a07451a82404a5"
          },
          "trip_id": {
            "type": "string",
            "example": "619f99ecc68548396ff542a4"
          },
          "payment_type": {
            "type": "string",
            "description": "Identificador del tipo de pago (ej. '1' para efectivo, '2' para tarjeta)",
            "example": "1"
          }
        }
      },
      "StandardResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "description": "Código de respuesta del sistema",
            "example": "62"
          }
        }
      }
    }
  }
}


```
