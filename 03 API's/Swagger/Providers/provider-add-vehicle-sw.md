### Registro de Vehículo de Proveedores

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Vehicle Registration API",
    "description": "API para que los proveedores registren nuevos vehículos",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Desarrollo/Producción"
    }
  ],
  "paths": {
    "/provider_add_vehicle": {
      "post": {
        "tags": [
          "Vehículos"
        ],
        "summary": "Agregar un nuevo vehículo",
        "description": "Registra un vehículo asociado a un proveedor y devuelve los detalles del vehículo creado junto con la lista de documentos necesarios.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddVehicleRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Vehículo registrado exitosamente.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AddVehicleResponse"
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
      "AddVehicleRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token",
          "vehicle_name",
          "plate_no"
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
            "example": ["handicap", "hotspot", "baby_seat"]
          }
        }
      },
      "AddVehicleResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "vehicle_detail": {
            "$ref": "#/components/schemas/VehicleDetail"
          },
          "document_list": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/VehicleDocument"
            }
          }
        }
      },
      "VehicleDetail": {
        "type": "object",
        "properties": {
          "_id": { "type": "string", "example": "61979e59e8eee70339aa885d" },
          "name": { "type": "string", "example": "Scooter" },
          "accessibility": {
            "type": "array",
            "items": { "type": "string" }
          },
          "plate_no": { "type": "string", "example": "1111" },
          "model": { "type": "string", "example": "Access" },
          "color": { "type": "string", "example": "Black" },
          "passing_year": { "type": "string", "example": "2018" },
          "service_type": { "type": "string", "nullable": true, "example": null },
          "admin_type_id": { "type": "string", "nullable": true, "example": null },
          "is_documents_expired": { "type": "boolean", "example": false },
          "is_selected": { "type": "boolean", "example": false },
          "is_document_uploaded": { "type": "boolean", "example": true }
        }
      },
      "VehicleDocument": {
        "type": "object",
        "properties": {
          "_id": { "type": "string", "example": "61979e59e8eee70339aa885e" },
          "vehicle_id": { "type": "string", "example": "61979e59e8eee70339aa885d" },
          "provider_id": { "type": "string", "example": "61979073da10546535a80fc1" },
          "document_id": { "type": "string", "example": "60239659d51a7042436be466" },
          "__v": { "type": "integer", "example": 0 },
          "updated_at": { "type": "string", "format": "date-time", "example": "2021-11-19T12:53:45.824Z" },
          "created_at": { "type": "string", "format": "date-time", "example": "2021-11-19T12:53:45.824Z" },
          "is_document_expired": { "type": "boolean", "example": false },
          "is_expired_date": { "type": "boolean", "example": true },
          "is_unique_code": { "type": "boolean", "example": true },
          "expired_date": { "type": "string", "nullable": true, "example": null },
          "unique_code": { "type": "string", "example": "" },
          "is_uploaded": { "type": "integer", "example": 0 },
          "document_picture": { "type": "string", "example": "" },
          "option": { "type": "integer", "example": 0 },
          "name": { "type": "string", "example": "Vehicle_ID" }
        }
      }
    }
  }
}

```
