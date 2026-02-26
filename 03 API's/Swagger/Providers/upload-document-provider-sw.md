### Cargar Documentos de Proveedores

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider Document API",
    "description": "Servicio la carga de documentos de proveedores.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de Desarrollo/Producción"
    }
  ],
  "paths": {
    "/uploaddocument": {
      "post": {
        "tags": [
          "Documentación"
        ],
        "summary": "Cargar documento del proveedor",
        "description": "Endpoint para subir imágenes de documentos legales (licencias, IDs) asociados a un proveedor específico.",
        "requestBody": {
          "required": true,
          "content": {
            "multipart/form-data": {
              "schema": {
                "$ref": "#/components/schemas/UploadRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Operación exitosa",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/UploadResponse"
                }
              }
            }
          },
          "401": {
            "description": "Token inválido (Error 451)",
            "content": {
              "application/json": {
                "example": {
                  "success": false,
                  "error_code": "451"
                }
              }
            }
          },
          "404": {
            "description": "Proveedor o Lista de documentos no encontrada (Errors 479/480)",
            "content": {
              "application/json": {
                "example": {
                  "success": false,
                  "error_code": "480"
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
      "UploadRequest": {
        "type": "object",
        "required": [
          "provider_id",
          "token",
          "document_id",
          "pictureData"
        ],
        "properties": {
          "provider_id": {
            "type": "string",
            "example": "{{PROVIDER_ID}}",
            "description": "Identificador único del proveedor."
          },
          "token": {
            "type": "string",
            "example": "{{PROVIDER_TOKEN}}",
            "description": "Token de sesión activo."
          },
          "document_id": {
            "type": "string",
            "example": "61979073da10546535a80fc2",
            "description": "ID del tipo de documento a cargar."
          },
          "unique_code": {
            "type": "string",
            "example": "1234",
            "description": "Número de serie o código único del documento físico."
          },
          "expired_date": {
            "type": "string",
            "format": "date-time",
            "example": "2021-11-30T23:59:00.197Z",
            "description": "Fecha de vencimiento en formato ISO 8601."
          },
          "pictureData": {
            "type": "string",
            "format": "binary",
            "description": "Archivo de imagen del documento."
          }
        }
      },
      "UploadResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "78",
            "description": "ID del registro de carga generado."
          },
          "document_picture": {
            "type": "string",
            "example": "provider_document/61979073da10546535a80fc2dumx.jpg"
          },
          "unique_code": {
            "type": "string",
            "example": "1234"
          },
          "expired_date": {
            "type": "string",
            "format": "date-time",
            "example": "2021-11-30T23:59:00.197Z"
          },
          "is_uploaded": {
            "type": "integer",
            "enum": [0, 1],
            "example": 1
          },
          "is_document_uploaded": {
            "type": "integer",
            "enum": [0, 1],
            "example": 1
          },
          "is_documents_expired": {
            "type": "boolean",
            "example": false
          }
        }
      }
    }
  }
}

```
