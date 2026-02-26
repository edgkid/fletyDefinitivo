
### Consulta de Área de Mayor Demanda

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Proveedores - área de mayor demanda",
    "description": "API para obtener las ubicaciones de mayor demanda.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/provider_heat_map": {
      "post": {
        "summary": "Obtener mapa de calor de recogidas",
        "operationId": "getProviderHeatMap",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/HeatMapRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Lista de ubicaciones de recogida obtenida exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/HeatMapResponse"
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
      "HeatMapRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "description": "ID del proveedor",
            "example": "{{PROVIDER_ID}}"
          },
          "token": {
            "type": "string",
            "description": "Token de autenticación",
            "example": "{{PROVIDER_TOKEN}}"
          }
        }
      },
      "HeatMapResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "pickup_locations": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "sourceLocation": {
                  "type": "array",
                  "description": "Coordenadas geográficas [Latitud, Longitud]",
                  "items": {
                    "type": "number",
                    "format": "double"
                  },
                  "example": [22.303646296825626, 70.8016881310633]
                }
              }
            }
          }
        }
      }
    }
  }
}
```
