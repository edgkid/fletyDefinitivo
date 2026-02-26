### Cambiar Estatus de Billetera

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "User Wallet API",
    "description": "API para gestionar el estaus de la billetera.",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "https://api.tu-dominio.com",
      "description": "Servidor de producción"
    }
  ],
  "paths": {
    "/change_user_wallet_status": {
      "post": {
        "summary": "Cambiar el estatus de la billetera del usuario",
        "operationId": "changeUserWalletStatus",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/WalletStatusRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Estado actualizado exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/WalletStatusResponse"
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
      "WalletStatusRequest": {
        "type": "object",
        "properties": {
          "user_id": {
            "type": "string",
            "example": "USER_12345"
          },
          "token": {
            "type": "string",
            "example": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
          },
          "is_use_wallet": {
            "type": "integer",
            "description": "Indica si se debe usar la billetera (1 para sí, 0 para no)",
            "enum": [0, 1],
            "example": 1
          }
        },
        "required": ["user_id", "token", "is_use_wallet"]
      },
      "WalletStatusResponse": {
        "type": "object",
        "properties": {
          "success": {
            "type": "boolean",
            "example": true
          },
          "message": {
            "type": "string",
            "example": "92"
          },
          "is_use_wallet": {
            "type": "integer",
            "description": "Estado final de la billetera",
            "enum": [0, 1],
            "example": 0
          }
        }
      }
    }
  }
}
```
