### Llamadas a Través de Twillio

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Notificaciones - Twilio Voice Service",
    "description": "Servicio de inicio de llamadas de voz automatizadas a través de Twilio.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "{{URL}}",
      "description": "Servidor de API"
    }
  ],
  "paths": {
    "/twilio_voice_call": {
      "post": {
        "summary": "Iniciar llamada de voz Twilio",
        "operationId": "initiateTwilioVoiceCall",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/VoiceCallRequest"
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
                  "$ref": "#/components/schemas/VoiceCallResponse"
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
      "VoiceCallRequest": {
        "type": "object",
        "required": [
          "trip_id",
          "type"
        ],
        "properties": {
          "trip_id": {
            "type": "string",
            "description": "Identificador único del viaje",
            "example": "{{TRIP_ID}}"
          },
          "type": {
            "type": "integer",
            "description": "Tipo de llamada o categoría de notificación",
            "example": 0
          }
        }
      },
      "VoiceCallResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          }
        }
      }
    }
  }
}

```
