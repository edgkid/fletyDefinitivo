### Actualizar Vehiculo de Proveedores

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Vehicle Management API - update",
    "description": "API para la actualización de vehículos por parte de los proveedores.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor base"
    }
  ],
  "paths": {
    "/provider_update_vehicle_detail": {
      "post": {
        "tags": [
          "Vehículos"
        ],
        "summary": "Actualizar detalles del vehículo",
        "description": "Permite a un proveedor actualizar la información técnica y de accesibilidad de un vehículo existente mediante su ID.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/UpdateVehicleRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Detalles del vehículo actualizados exitosamente.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/UpdateVehicleResponse"
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
      "UpdateVehicleRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token",
          "vehicle_id"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}"
          },
          "token": {
            "type": "string",
            "example": "{{PROVIDER_TOKEN}}"
          },
          "vehicle_name": {
            "type": "string",
            "example": "Scooter"
          },
          "vehicle_id": {
            "type": "string",
            "example": "61979c72e096a97e07f0df06"
          },
          "plate_no": {
            "type": "string",
            "example": "1111"
          },
          "model": {
            "type": "string",
            "example": "Access"
          },
          "color": {
            "type": "string",
            "example": "Black"
          },
          "passing_year": {
            "type": "string",
            "example": "2018"
          },
          "accessibility": {
            "type": "array",
            "items": {
              "type": "string"
            },
            "example": [
              "handicap",
              "hotspot",
              "baby_seat"
            ]
          }
        }
      },
      "UpdateVehicleResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "vehicle_detail": {
            "$ref": "#/components/schemas/VehicleDetail"
          }
        }
      },
      "VehicleDetail": {
        "type": "object",
        "properties": {
          "_id": {
            "type": "string",
            "example": "61979c72e096a97e07f0df06"
          },
          "name": {
            "type": "string",
            "example": "Scooter"
          },
          "accessibility": {
            "type": "array",
            "items": {
              "type": "string"
            },
            "example": [
              "handicap",
              "hotspot",
              "baby_seat"
            ]
          },
          "plate_no": {
            "type": "string",
            "example": "1111"
          },
          "model": {
            "type": "string",
            "example": "Access"
          },
          "color": {
            "type": "string",
            "example": "Black"
          },
          "passing_year": {
            "type": "string",
            "example": "2018"
          },
          "service_type": {
            "type": "string",
            "nullable": true,
            "example": null
          },
          "admin_type_id": {
            "type": "string",
            "nullable": true,
            "example": null
          },
          "is_documents_expired": {
            "type": "boolean",
            "example": false
          },
          "is_selected": {
            "type": "boolean",
            "example": false
          },
          "is_document_uploaded": {
            "type": "boolean",
            "example": true
          }
        }
      }
    }
  }
}

```
