### Consulta Estatus del Viaje

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de esatus de Viaje y Ciudad",
    "description": "Endpoint para obtener detalles en tiempo real sobre un viaje activo y las configuraciones de negocio de la ciudad.",
    "version": "1.0.0"
  },
  "paths": {
    "/get_trip_details": {
      "post": {
        "summary": "Obtener detalles del viaje",
        "operationId": "getTripDetails",
        "tags": ["Trips"],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/TripStatusRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Detalles del viaje y configuración de ciudad recuperados",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/TripStatusResponse"
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
      "TripStatusRequest": {
        "type": "object",
        "properties": {
          "user_id": { "type": "string", "example": "61978529e3a0..." },
          "token": { "type": "string", "example": "eJLAFZFkPUjj..." }
        },
        "required": ["user_id", "token"]
      },
      "TripStatusResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "message": { "type": "string", "example": "10" },
          "map_pin_image_url": { "type": "string", "example": "service_type_map_pin_images/image.png" },
          "city_detail": { "$ref": "#/components/schemas/CityDetail" },
          "trip": { "$ref": "#/components/schemas/TripDetail" }
        }
      },
      "CityDetail": {
        "type": "object",
        "properties": {
          "_id": { "type": "string" },
          "cityname": { "type": "string", "example": "Rajkot" },
          "full_cityname": { "type": "string", "example": "Rajkot, Gujarat" },
          "countryname": { "type": "string", "example": "India" },
          "cityLatLong": {
            "type": "array",
            "items": { "type": "number" },
            "example": [22.3038945, 70.8021598]
          },
          "timezone": { "type": "string" },
          "is_payment_mode_cash": { "type": "integer", "example": 1 },
          "is_payment_mode_card": { "type": "integer", "example": 1 },
          "cityRadius": { "type": "number", "example": 50 },
          "is_ask_user_for_fixed_fare": { "type": "boolean" }
        }
      },
      "TripDetail": {
        "type": "object",
        "properties": {
          "_id": { "type": "string" },
          "unique_id": { "type": "integer" },
          "service_type_id": { "type": "string" },
          "sourceLocation": {
            "type": "array",
            "items": { "type": "number" },
            "example": [22.3039, 70.8020]
          },
          "payment_mode": { "type": "integer" },
          "total": { "type": "number", "example": 0 },
          "promo_payment": { "type": "number", "example": 0 },
          "is_amount_refund": { "type": "boolean" },
          "created_at": { "type": "string", "format": "date-time" },
          "updated_at": { "type": "string", "format": "date-time" }
        }
      }
    }
  }
}


```
