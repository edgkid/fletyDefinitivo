### Usar Código de Referido

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API -aplica codigo de referencia.",
    "version": "1.0.0",
    "description": "Documentación para el endpoint de aplicación de código de referencia."
  },
  "servers": [
    {
      "url": "{URL}",
      "description": "Servidor principal de la API. Reemplazar {URL} con la URL base real."
    }
  ],
  "paths": {
    "/apply_referral_code": {
      "post": {
        "summary": "Aplica un código de referencia o lo salta.",
        "operationId": "applyReferralCode",
        "requestBody": {
          "description": "Datos necesarios para aplicar o saltar el código de referencia.",
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "user_id": {
                    "type": "string",
                    "description": "ID único del usuario.",
                    "example": "619b8f896ce71713fa2b59ce"
                  },
                  "token": {
                    "type": "string",
                    "description": "Token de autenticación del usuario.",
                    "example": "Gn3sFrQnfd2GbNsrk2YKdg3SRHmxoQGi"
                  },
                  "referral_code": {
                    "type": "string",
                    "description": "El código de referencia a aplicar. Puede estar vacío o ser nulo si 'is_skip' es 1.",
                    "example": "I8IXPZFV"
                  },
                  "is_skip": {
                    "type": "integer",
                    "format": "int32",
                    "description": "Indica si se está omitiendo la aplicación del código de referencia (1 = omitir, 0 = aplicar).",
                    "example": 0
                  }
                },
                "required": [
                  "user_id",
                  "token",
                  "is_skip"
                ]
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Respuesta exitosa al aplicar o saltar el código de referencia.",
            "content": {
              "application/json": {
                "schema": {
                  "oneOf": [
                    {
                      "$ref": "#/components/schemas/SuccessResponse"
                    },
                    {
                      "$ref": "#/components/schemas/SuccessResponseSkip"
                    }
                  ]
                },
                "examples": {
                  "successApplied": {
                    "summary": "Aplicación de Código Exitosa",
                    "value": {
                      "success": true,
                      "message": "12",
                      "user_id": "619b8f896ce71713fa2b59ce",
                      "is_referral": 1,
                      "first_name": "Test",
                      "last_name": "Test",
                      "country_phone_code": "+58",
                      "phone": "1234567890",
                      "email": "t1est@gmail.com",
                      "picture": "",
                      "bio": "",
                      "address": "",
                      "city": "",
                      "country": "Venezuela, Bolivarian Republic of Venezuela",
                      "zipcode": "",
                      "login_by": "manual",
                      "social_unique_id": "",
                      "device_token": "f2S87ZELQWK88VQsYtufi3:APA91bElwa_FcdsTNeVdwjOod8Eiq-8Nn_5W9U-_jSPN1GdzQ0qIjWEppPLusGi45P9YKSqtoVkmLTxjzxdC0BD5P_NkWCJPPlAod9UiBgZpeP-b5flOOY8aGhwB7r6FmUQKwyJhMiMN",
                      "device_type": "android",
                      "referral_code": "SRIQMJQG",
                      "device_timezone": "Asia/Kolkata"
                    }
                  },
                  "successSkipped": {
                    "summary": "Omisión de Código Exitosa",
                    "value": {
                      "success": true,
                      "message": "13",
                      "user_id": "619b8f896ce71713fa2b59ce",
                      "is_referral": 1,
                      "first_name": "Test",
                      "last_name": "Test",
                      "country_phone_code": "+58",
                      "phone": "1234567890",
                      "email": "t1est@gmail.com",
                      "picture": "",
                      "bio": "",
                      "address": "",
                      "city": "",
                      "country": "Venezuela, Bolivarian Republic of Venezuela",
                      "zipcode": "",
                      "login_by": "manual",
                      "social_unique_id": "",
                      "device_token": "f2S87ZELQWK88VQsYtufi3:APA91bElwa_FcdsTNeVdwjOod8Eiq-8Nn_5W9U-_jSPN1GdzQ0qIjWEppPLusGi45P9YKSqtoVkmLTxjzxdC0BD5P_NkWCJPPlAod9UiBgZpeP-b5flOOY8aGhwB7r6FmUQKwyJhMiMN",
                      "device_type": "android",
                      "referral_code": "SRIQMJQG",
                      "device_timezone": "Asia/Kolkata"
                    }
                  }
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
      "UserProfile": {
        "type": "object",
        "properties": {
          "user_id": {
            "type": "string"
          },
          "is_referral": {
            "type": "integer",
            "description": "Estado del referido (1 = aplicado)."
          },
          "first_name": {
            "type": "string"
          },
          "last_name": {
            "type": "string"
          },
          "country_phone_code": {
            "type": "string"
          },
          "phone": {
            "type": "string"
          },
          "email": {
            "type": "string"
          },
          "picture": {
            "type": "string"
          },
          "bio": {
            "type": "string"
          },
          "address": {
            "type": "string"
          },
          "city": {
            "type": "string"
          },
          "country": {
            "type": "string"
          },
          "zipcode": {
            "type": "string"
          },
          "login_by": {
            "type": "string"
          },
          "social_unique_id": {
            "type": "string"
          },
          "device_token": {
            "type": "string"
          },
          "device_type": {
            "type": "string"
          },
          "referral_code": {
            "type": "string",
            "description": "El código de referencia generado/del usuario."
          },
          "device_timezone": {
            "type": "string"
          }
        }
      },
      "SuccessResponse": {
        "allOf": [
          {
            "$ref": "#/components/schemas/UserProfile"
          },
          {
            "type": "object",
            "properties": {
              "success": {
                "type": "boolean",
                "example": true
              },
              "message": {
                "type": "string",
                "description": "Mensaje de código '12' para aplicación exitosa.",
                "example": "12"
              }
            }
          }
        ]
      },
      "SuccessResponseSkip": {
        "allOf": [
          {
            "$ref": "#/components/schemas/UserProfile"
          },
          {
            "type": "object",
            "properties": {
              "success": {
                "type": "boolean",
                "example": true
              },
              "message": {
                "type": "string",
                "description": "Mensaje de código '13' para omisión exitosa.",
                "example": "13"
              }
            }
          }
        ]
      }
    }
  }
}

```
