

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Rastreo - Ubicación del Proveedor",
    "description": "Servicio para actualizar y consultar la ubicación de un proveedor.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/provider_location": {
      "post": {
        "summary": "Actualizar ubicación del proveedor",
        "operationId": "updateProviderLocation",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/LocationUpdateRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Ubicación procesada correctamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/LocationUpdateResponse"
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
      "LocationUpdateRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "latitude",
          "longitude",
          "trip_id"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "example": "6034e30123891d70e65038b2"
          },
          "latitude": {
            "type": "number",
            "format": "double",
            "example": 22.2851115375326
          },
          "longitude": {
            "type": "number",
            "format": "double",
            "example": 70.77722978158
          },
          "trip_id": {
            "type": "string",
            "example": "{{TRIP_ID}}"
          },
          "location_unique_id": {
            "type": "integer",
            "example": 1
          },
          "location": {
            "type": "array",
            "items": {
              "type": "number",
              "format": "double"
            },
            "example": [22.07777, 77.2323222]
          }
        }
      },
      "LocationUpdateResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "in_zone_queue": {
            "type": "boolean",
            "example": false
          },
          "zone_queue_no": {
            "type": "integer",
            "nullable": true,
            "example": null
          },
          "location_unique_id": {
            "type": "string",
            "example": "1"
          },
          "providerLocation": {
            "type": "array",
            "items": {
              "type": "number",
              "format": "double"
            },
            "example": [22.2851115375326, 70.77722978158]
          }
        }
      }
    }
  }
}

```
