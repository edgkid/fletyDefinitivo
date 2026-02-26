
### Ganancias Semanales de un Proveedor

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider Earning API",
    "description": "Endpoint para obtener el desglose detallado de las ganancias semanales de un proveedor.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Reportes"
    }
  ],
  "paths": {
    "/get_provider_weekly_earning_detail": {
      "post": {
        "summary": "Obtener detalle de ganancias semanales",
        "operationId": "getWeeklyEarningDetail",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/EarningRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Reporte generado exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/EarningResponse"
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
      "EarningRequest": {
        "type": "object",
        "required": ["provider_id", "token", "date"],
        "properties": {
          "provider_id": { "type": "string", "example": "{{PROVIDER_ID}}" },
          "token": { "type": "string", "example": "{{PROVIDER_TOKEN}}" },
          "date": { "type": "string", "example": "21 Nov 2021" }
        }
      },
      "EarningResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "currency": { "type": "string", "example": "₹" },
          "currencycode": { "type": "string", "example": "INR" },
          "provider_weekly_analytic": { "$ref": "#/components/schemas/WeeklyAnalytic" },
          "provider_weekly_earning": { "$ref": "#/components/schemas/WeeklyEarning" },
          "date": { "$ref": "#/components/schemas/WeeklyDates" },
          "trip_day_total": { "$ref": "#/components/schemas/TripDayTotal" }
        }
      },
      "WeeklyAnalytic": {
        "type": "object",
        "properties": {
          "received": { "type": "integer" },
          "accepted": { "type": "integer" },
          "rejected": { "type": "integer" },
          "completed": { "type": "integer" },
          "acception_ratio": { "type": "number" },
          "total_online_time": { "type": "integer", "description": "Tiempo en segundos" }
        }
      },
      "WeeklyEarning": {
        "type": "object",
        "properties": {
          "service_total": { "type": "number" },
          "total_toll_amount": { "type": "number" },
          "total_provider_service_fees": { "type": "number" },
          "total_provider_have_cash": { "type": "number" },
          "total_paid_in_wallet_payment": { "type": "number" },
          "statement_number": { "type": "string" }
        }
      },
      "WeeklyDates": {
        "type": "object",
        "properties": {
          "date1": { "type": "string", "format": "date-time" },
          "date2": { "type": "string", "format": "date-time" },
          "date3": { "type": "string", "format": "date-time" },
          "date4": { "type": "string", "format": "date-time" },
          "date5": { "type": "string", "format": "date-time" },
          "date6": { "type": "string", "format": "date-time" },
          "date7": { "type": "string", "format": "date-time" }
        }
      },
      "TripDayTotal": {
        "type": "object",
        "properties": {
          "date1": { "type": "number" },
          "date2": { "type": "number" },
          "date3": { "type": "number" },
          "date4": { "type": "number" },
          "date5": { "type": "number" },
          "date6": { "type": "number" },
          "date7": { "type": "number" }
        }
      }
    }
  }
}

```
