### Detalle de Viajes y Ganancias Diarias

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider Daily Earning API",
    "description": "API para obtener detalle diario de ganancias y  viajes realizados de un proveedor.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Operaciones"
    }
  ],
  "paths": {
    "/get_provider_daily_earning_detail": {
      "post": {
        "summary": "Obtener detalles de ganancias diarias",
        "operationId": "getDailyEarningDetail",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/DailyEarningRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Resumen diario recuperado exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/DailyEarningResponse"
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
      "DailyEarningRequest": {
        "type": "object",
        "required": ["provider_id", "token", "date"],
        "properties": {
          "provider_id": { "type": "string", "example": "{{PROVIDER_ID}}" },
          "token": { "type": "string", "example": "{{PROVIDER_TOKEN}}" },
          "date": { "type": "string", "example": "25 Nov 2021" }
        }
      },
      "DailyEarningResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "currency": { "type": "string", "example": "₹" },
          "currencycode": { "type": "string", "example": "INR" },
          "provider_daily_analytic": { "$ref": "#/components/schemas/DailyAnalytic" },
          "provider_daily_earning": { "$ref": "#/components/schemas/DailyEarningSummary" },
          "trips": {
            "type": "array",
            "items": { "$ref": "#/components/schemas/TripMinimalDetail" }
          }
        }
      },
      "DailyAnalytic": {
        "type": "object",
        "properties": {
          "total_online_time": { "type": "integer" },
          "completed_ratio": { "type": "number" },
          "acception_ratio": { "type": "number" },
          "completed": { "type": "integer" },
          "received": { "type": "integer" },
          "date_tag": { "type": "string", "example": "Nov 25, 2021" }
        }
      },
      "DailyEarningSummary": {
        "type": "object",
        "properties": {
          "service_total": { "type": "number" },
          "total_provider_service_fees": { "type": "number" },
          "total_provider_have_cash": { "type": "number" },
          "total_paid_in_wallet_payment": { "type": "number" },
          "statement_number": { "type": "string" }
        }
      },
      "TripMinimalDetail": {
        "type": "object",
        "properties": {
          "unique_id": { "type": "integer" },
          "payment_mode": { "type": "integer" },
          "provider_service_fees": { "type": "number" },
          "total": { "type": "number" },
          "provider_income_set_in_wallet": { "type": "number" },
          "pay_to_provider": { "type": "number" },
          "provider_have_cash": { "type": "number" }
        }
      }
    }
  }
}

```
