### Dispersar Pagos (Payu)

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Proveedores - Configuración PayU",
    "description": "Servicio para vincular y registrar los detalles de la cuenta bancaria del proveedor para la dispersión de pagos. ",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Producción/Sandbox"
    }
  ],
  "paths": {
    "/add_bank_detail": {
      "post": {
        "summary": "Vincular cuenta bancaria PayU",
        "operationId": "addBankDetailPayU",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/BankDetailRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Operación exitosa",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/BankDetailResponse"
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
      "BankDetailRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "payment_gateway_type",
          "account_number",
          "bank_code",
          "password"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "description": "ID único del proveedor",
            "example": "{{PROVIDER_ID}}"
          },
          "payment_gateway_type": {
            "type": "integer",
            "description": "Tipo de pasarela (12 para PayU)",
            "example": 12
          },
          "account_number": {
            "type": "string",
            "description": "Número de cuenta con soporte para ceros a la izquierda",
            "example": "000123456789"
          },
          "bank_code": {
            "type": "string",
            "description": "Código identificador de la entidad bancaria",
            "example": "789"
          },
          "password": {
            "type": "string",
            "format": "password",
            "description": "Contraseña de seguridad del usuario",
            "example": "123456"
          }
        }
      },
      "BankDetailResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          }
        }
      }
    }
  }
}

```
