### Agregar Contacto de Emergencia

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - Agreagr contacto de emergencia",
    "version": "1.0.0",
    "description": "API para agregar un nuevo contacto de emergencia a un usuario."
  },
  "servers": [
    {
      "url": "{URL}",
      "variables": {
        "URL": {
          "default": "https://api.ejemplo.com",
          "description": "URL base de la API."
        }
      }
    }
  ],
  "paths": {
    "/add_emergency_contact": {
      "post": {
        "summary": "Agregar Contacto de Emergencia",
        "description": "Permite al usuario añadir un nuevo contacto de emergencia, con la opción de compartir automáticamente los detalles del viaje.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AddEmergencyContactRequest"
              },
              "example": {
                "user_id": "{{USER_ID}}",
                "token": "{{USER_TOKEN}}",
                "name": "Test",
                "phone": "3022874531",
                "is_always_share_ride_detail": 1
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Resultado de la operación. Puede ser una lista de éxito o error.",
            "content": {
              "application/json": {
                "schema": {
                  "type": "array",
                  "items": {
                    "oneOf": [
                      {
                        "$ref": "#/components/schemas/SuccessResponse"
                      },
                      {
                        "$ref": "#/components/schemas/ErrorResponse"
                      }
                    ]
                  }
                },
                "example": [
                  {
                    "success": true,
                    "message": "67",
                    "emergency_contact_data": {
                      "__v": 0,
                      "user_id": "61962d683b0daa5338204ce6",
                      "_id": "61965bc435a1c02ca00d3483",
                      "updated_at": "2021-11-18T13:57:24.893Z",
                      "created_at": "2021-11-18T13:57:24.893Z",
                      "is_always_share_ride_detail": 1,
                      "phone": "3022874531",
                      "name": "Test"
                    }
                  }
                ]
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "AddEmergencyContactRequest": {
        "type": "object",
        "properties": {
          "user_id": {
            "type": "string",
            "description": "Identificador único del usuario."
          },
          "token": {
            "type": "string",
            "description": "Token de autenticación del usuario."
          },
          "name": {
            "type": "string",
            "description": "Nombre del contacto de emergencia."
          },
          "phone": {
            "type": "string",
            "description": "Número de teléfono del contacto de emergencia."
          },
          "is_always_share_ride_detail": {
            "type": "integer",
            "format": "int32",
            "enum": [0, 1],
            "description": "Indica si siempre se deben compartir los detalles del viaje con este contacto (1=Sí, 0=No)."
          }
        },
        "required": [
          "user_id",
          "token",
          "name",
          "phone",
          "is_always_share_ride_detail"
        ]
      },
      "EmergencyContactData": {
        "type": "object",
        "properties": {
          "__v": {
            "type": "integer"
          },
          "user_id": {
            "type": "string"
          },
          "_id": {
            "type": "string",
            "description": "ID del contacto de emergencia recién creado."
          },
          "updated_at": {
            "type": "string",
            "format": "date-time"
          },
          "created_at": {
            "type": "string",
            "format": "date-time"
          },
          "is_always_share_ride_detail": {
            "type": "integer",
            "format": "int32"
          },
          "phone": {
            "type": "string"
          },
          "name": {
            "type": "string"
          }
        }
      },
      "SuccessResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "enum": [true]
          },
          "message": {
            "type": "string",
            "description": "Código de mensaje o estado de éxito."
          },
          "emergency_contact_data": {
            "$ref": "#/components/schemas/EmergencyContactData"
          }
        },
        "required": [
          "success",
          "message",
          "emergency_contact_data"
        ]
      },
      "ErrorResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "enum": [false]
          },
          "error_code": {
            "type": "string",
            "description": "Código de error específico (ej. 468, 497)."
          }
        },
        "required": [
          "success",
          "error_code"
        ]
      }
    }
  }
}


```
