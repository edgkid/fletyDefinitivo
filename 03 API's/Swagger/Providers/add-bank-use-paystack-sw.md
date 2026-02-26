
### Dispersar Pagos (Paystack)

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Proveedores - Gestión Bancaria",
    "description": "Servicio para vincular y registrar los detalles de la cuenta bancaria del proveedor para la dispersión de pagos.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/add_bank_detail": {
      "post": {
        "summary": "Agregar detalles bancarios",
        "operationId": "addBankDetail",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddBankRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Cuenta bancaria registrada exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddBankResponse"
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
      "AddBankRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "account_number",
          "bank_code",
          "password"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}"
          },
          "payment_gateway_type": {
            "type": "integer",
            "description": "ID de la pasarela de pago (ej. 11 para Paystack/Stripe Custom)",
            "example": 11
          },
          "account_holder_type": {
            "type": "string",
            "enum": ["individual", "company"],
            "example": "individual"
          },
          "web": {
            "type": "integer",
            "description": "Indicador de origen (1 para web, 0 para móvil)",
            "example": 1
          },
          "account_number": {
            "type": "string",
            "description": "Número de cuenta bancaria",
            "example": "2254866359"
          },
          "bank_code": {
            "type": "string",
            "description": "Código de identificación del banco",
            "example": "057"
          },
          "password": {
            "type": "string",
            "format": "password",
            "description": "Contraseña de confirmación del proveedor",
            "example": "123456"
          }
        }
      },
      "AddBankResponse": {
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
