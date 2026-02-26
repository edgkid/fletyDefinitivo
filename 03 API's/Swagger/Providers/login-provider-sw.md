### Inicio de Sesión

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API de Proveedores login",
    "description": "Servicio para autenticación proveedores/conductores.",
    "version": "1.0.0"
  },
  "paths": {
    "/providerslogin": {
      "post": {
        "summary": "Inicio de sesión de proveedor",
        "operationId": "providerLogin",
        "description": "Permite a un proveedor autenticarse en la aplicación mediante credenciales manuales o redes sociales.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "email": { "type": "string", "format": "email", "example": "nick@driver.com" },
                  "password": { "type": "string", "format": "password", "example": "123456" },
                  "device_type": { "type": "string", "enum": ["android", "ios"], "example": "android" },
                  "device_token": { "type": "string", "example": "f5cKdH3CRqaE7e4XfDg6HU:APA91..." },
                  "login_by": { "type": "string", "example": "manual" },
                  "app_version": { "type": "string", "example": "1.1.9" }
                },
                "required": ["email", "password", "device_type", "device_token", "login_by"]
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Login exitoso",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "success": { "type": "boolean", "example": true },
                    "provider_detail": { "$ref": "#/components/schemas/ProviderDetail" },
                    "phone_number_min_length": { "type": "integer", "example": 10 },
                    "phone_number_length": { "type": "integer", "example": 10 }
                  }
                }
              }
            }
          },
          "401": {
            "description": "Credenciales inválidas"
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "ProviderDetail": {
        "type": "object",
        "properties": {
          "first_name": { "type": "string", "example": "Nick" },
          "last_name": { "type": "string", "example": "Duo" },
          "email": { "type": "string", "example": "nick@driver.com" },
          "country_phone_code": { "type": "string", "example": "+91" },
          "is_document_uploaded": { "type": "integer", "example": 1 },
          "address": { "type": "string", "example": "Rajkot" },
          "is_approved": { "type": "integer", "example": 0 },
          "_id": { "type": "string", "example": "61979073da10546535a80fc1" },
          "social_unique_id": { "type": "string", "example": "" },
          "phone": { "type": "string", "example": "9876543210" },
          "login_by": { "type": "string", "example": "manual" },
          "is_documents_expired": { "type": "boolean", "example": false },
          "account_id": { "type": "string", "example": "" },
          "bank_id": { "type": "string", "example": "" },
          "is_referral": { "type": "integer", "example": 1 },
          "referral_code": { "type": "string", "example": "M44W0YRU" },
          "city": { "type": "string", "example": "Rajkot" },
          "country": { "type": "string", "example": "India" },
          "rate": { "type": "number", "example": 0 },
          "rate_count": { "type": "integer", "example": 0 },
          "token": { "type": "string", "example": "oi184TNPRxplTqDDnJKkwDcIKUgOsl3W" },
          "is_vehicle_document_uploaded": { "type": "boolean", "example": false },
          "service_type": { "type": "string", "nullable": true, "example": null },
          "admintypeid": { "type": "string", "nullable": true, "example": null },
          "is_available": { "type": "integer", "example": 1 },
          "is_active": { "type": "integer", "example": 0 },
          "is_partner_approved_by_admin": { "type": "integer", "example": 1 },
          "picture": { "type": "string", "example": "" },
          "wallet_currency_code": { "type": "string", "example": "INR" },
          "country_detail": {
            "type": "object",
            "properties": {
              "is_referral": { "type": "boolean", "example": true }
            }
          }
        }
      }
    }
  }
}


```
