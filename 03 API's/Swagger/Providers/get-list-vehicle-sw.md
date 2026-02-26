### Consulta Listado de Vehículos de Proveedor

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider Vehicle API - get list",
    "description": "API para consultar el listado de vehículos registrados por un proveedor.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/get_provider_vehicle_list": {
      "post": {
        "tags": [
          "Vehículos"
        ],
        "summary": "Obtener lista de vehículos del proveedor",
        "description": "Devuelve todos los vehículos asociados al proveedor autenticado mediante su ID y token.",
        "requestBody": {
          "required": true,
          "content": {
            "multipart/form-data": {
              "schema": {
                "type": "object",
                "required": [
                  "provider_id",
                  "token"
                ],
                "properties": {
                  "provider_id": {
                    "type": "string",
                    "description": "Identificador único del proveedor.",
                    "example": "{{PROVIDER_ID}}"
                  },
                  "token": {
                    "type": "string",
                    "description": "Token de sesión activo del proveedor.",
                    "example": "{{PROVIDER_TOKEN}}"
                  }
                }
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Operación exitosa. Devuelve la lista de vehículos.",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/VehicleListResponse"
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
      "VehicleListResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "vehicle_list": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/VehicleListItem"
            }
          }
        }
      },
      "VehicleListItem": {
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
          "is_selected": {
            "type": "boolean",
            "example": false
          },
          "is_documents_expired": {
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
