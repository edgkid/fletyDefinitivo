### Detalle de Viaje del Proveedor

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider Trip Detail API",
    "description": "API para obtener el detalle del viaje del viaje del proveedor.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Producción"
    }
  ],
  "paths": {
    "/providertripdetail": {
      "post": {
        "summary": "Obtener detalles del viaje para el proveedor",
        "operationId": "getProviderTripDetail",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/TripDetailRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Detalles del viaje recuperados exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/TripDetailResponse"
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
      "TripDetailRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token",
          "trip_id"
        ],
        "properties": {
          "provider_id": { "type": "string", "example": "{{PROVIDER_ID}}" },
          "token": { "type": "string", "example": "{{PROVIDER_TOKEN}}" },
          "trip_id": { "type": "string", "example": "{{TRIP_ID}}" }
        }
      },
      "TripDetailResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "message": { "type": "string", "example": "30" },
          "trip": { "$ref": "#/components/schemas/TripObject" },
          "tripservice": { "$ref": "#/components/schemas/TripServiceObject" },
          "user": { "$ref": "#/components/schemas/UserObject" },
          "startTripToEndTripLocations": {
            "type": "array",
            "items": {
              "type": "array",
              "items": { "type": "number" }
            }
          }
        }
      },
      "TripObject": {
        "type": "object",
        "properties": {
          "_id": { "type": "string" },
          "unique_id": { "type": "integer" },
          "sourceLocation": { "type": "array", "items": { "type": "number" } },
          "destinationLocation": { "type": "array", "items": { "type": "number" } },
          "payment_mode": { "type": "integer" },
          "total": { "type": "number" },
          "cash_payment": { "type": "number" },
          "currency": { "type": "string" },
          "is_trip_completed": { "type": "integer" },
          "invoice_number": { "type": "string" }
        }
      },
      "TripServiceObject": {
        "type": "object",
        "properties": {
          "_id": { "type": "string" },
          "service_type_name": { "type": "string" },
          "base_price": { "type": "number" },
          "min_fare": { "type": "number" }
        }
      },
      "UserObject": {
        "type": "object",
        "properties": {
          "_id": { "type": "string" },
          "first_name": { "type": "string" },
          "last_name": { "type": "string" },
          "email": { "type": "string" },
          "phone": { "type": "string" },
          "rate": { "type": "number" }
        }
      }
    }
  }
}

```

