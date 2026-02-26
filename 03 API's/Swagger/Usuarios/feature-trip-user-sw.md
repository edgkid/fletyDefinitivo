### Consulta de Viajes Futuros

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Future Trips API",
    "description": "API para obtener el listado de viajes programados (futuros) de un usuario.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/getfuturetrip": {
      "post": {
        "summary": "Obtener viajes programados",
        "description": "Retorna una lista de todos los viajes que el usuario ha programado para el futuro.",
        "operationId": "getFutureTrips",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/FutureTripRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Lista de viajes programados obtenida con éxito",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/FutureTripResponse"
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
      "FutureTripRequest": {
        "type": "object",
        "required": [
          "user_id",
          "token"
        ],
        "properties": {
          "user_id": {
            "type": "string",
            "example": "{{USER_ID}}"
          },
          "token": {
            "type": "string",
            "example": "{{USER_TOKEN}}"
          }
        }
      },
      "FutureTripResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "43"
          },
          "scheduledtrip": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/ScheduledTrip"
            }
          }
        }
      },
      "ScheduledTrip": {
        "type": "object",
        "properties": {
          "_id": { "type": "string", "example": "619e4978a3a3924e076c5593" },
          "unique_id": { "type": "integer", "example": 292 },
          "updated_at": { "type": "string", "format": "date-time" },
          "user_id": { "type": "string" },
          "trip_type": { "type": "integer" },
          "sourceLocation": {
            "type": "array",
            "items": { "type": "number" },
            "example": [22.303880736325684, 70.80195339033952]
          },
          "destinationLocation": {
            "type": "array",
            "items": { "type": "number" },
            "example": [22.3039, 70.8022]
          },
          "payment_mode": { "type": "integer" },
          "schedule_start_time": { "type": "string", "format": "date-time", "example": "1970-01-02T16:12:45.050Z" },
          "server_start_time_for_schedule": { "type": "string", "format": "date-time" },
          "source_address": { "type": "string" },
          "destination_address": { "type": "string" },
          "total": { "type": "number" },
          "currency": { "type": "string" },
          "is_schedule_trip": { "type": "boolean" },
          "user_first_name": { "type": "string" },
          "user_last_name": { "type": "string" },
          "payment_gateway_type": { "type": "integer" },
          "is_trip_completed": { "type": "integer" },
          "is_trip_cancelled": { "type": "integer" }
        }
      }
    }
  }
}

```
