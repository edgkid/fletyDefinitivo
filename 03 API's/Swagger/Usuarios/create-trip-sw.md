### Crear un Viaje

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Gestión para la creación de Viajes",
    "description": "Definición para la solicitud de creación de un nuevo viaje basado en coordenadas de origen y destino.",
    "version": "1.0.0"
  },
  "paths": {
    "/create_trip": {
      "post": {
        "summary": "Crear un nuevo viaje",
        "operationId": "createTrip",
        "tags": ["Trips"],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/TripRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Viaje creado exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/TripResponse"
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
      "TripRequest": {
        "type": "object",
        "properties": {
          "d_latitude": { "type": "number", "format": "double", "example": 22.3039 },
          "d_longitude": { "type": "number", "format": "double", "example": 70.8022 },
          "destination_address": { "type": "string", "example": "Rajkot" },
          "user_id": { "type": "string", "example": "619e48cca..." },
          "token": { "type": "string", "example": "eyJhbG..." },
          "latitude": { "type": "number", "format": "double", "example": 22.30392912137144 },
          "longitude": { "type": "number", "format": "double", "example": 70.80200430434408 },
          "source_address": { "type": "string", "example": "Hospital Chowk, Doctors Quarters, Rajkot" },
          "timezone": { "type": "string", "example": "Asia/Kolkata" },
          "payment_mode": { "type": "integer", "example": 1, "description": "1: Cash, 2: Card" },
          "service_type_id": { "type": "string", "example": "602278c765b27b2840e6ea1e" },
          "is_surge_hours": { "type": "integer", "example": 0 },
          "surge_multiplier": { "type": "number", "example": 0 },
          "is_fixed_fare": { "type": "boolean", "example": false },
          "fixed_price": { "type": "number", "example": 0 },
          "accessibility": { "type": "array", "items": { "type": "string" }, "example": [] },
          "received_trip_from_gender": { "type": "array", "items": { "type": "string" }, "example": [] },
          "provider_language": { "type": "array", "items": { "type": "string" }, "example": [] },
          "is_trip_inside_zone_queue": { "type": "boolean", "example": false }
        },
        "required": ["user_id", "token", "latitude", "longitude", "d_latitude", "d_longitude", "service_type_id"]
      },
      "TripResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "message": { "type": "string", "example": "9" },
          "trip_id": { "type": "string", "example": "619e48cca3a3924e076c558f" }
        }
      }
    }
  }
}


```
