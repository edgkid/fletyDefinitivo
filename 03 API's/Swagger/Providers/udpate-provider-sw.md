### Actualizar Proveedor

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Provider API - update provider",
    "version": "1.0.0",
    "description": "API para la actualización de información del proveedor"
  },
  "paths": {
    "/providerupdatedetail": {
      "post": {
        "summary": "Actualizar detalles del proveedor",
        "operationId": "updateProviderDetail",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/UpdateProviderRequest"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Detalles actualizados exitosamente",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/UpdateProviderResponse"
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
      "UpdateProviderRequest": {
        "type": "object",
        "properties": {
          "provider_id": { "type": "string", "example": "{{PROVIDER_ID}}" },
          "token": { "type": "string", "example": "{{PROVIDER_TOKEN}}" },
          "first_name": { "type": "string", "example": "Nick" },
          "last_name": { "type": "string", "example": "Duo" },
          "old_password": { "type": "string", "example": "123456" },
          "new_password": { "type": "string", "example": "" },
          "address": { "type": "string", "example": "Rajkot" },
          "zipcode": { "type": "string", "example": "" },
          "phone": { "type": "string", "example": "9876543210" },
          "country_phone_code": { "type": "string", "example": "+91" },
          "bio": { "type": "string", "example": "" }
        }
      },
      "UpdateProviderResponse": {
        "type": "object",
        "properties": {
          "success": { "type": "boolean", "example": true },
          "message": { "type": "string", "example": "19" },
          "provider_detail": {
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
              "city": { "type": "string", "example": "Rajkot" },
              "country": { "type": "string", "example": "India" },
              "rate": { "type": "integer", "example": 0 },
              "referral_code": { "type": "string", "example": "M44W0YRU" },
              "rate_count": { "type": "integer", "example": 0 },
              "token": { "type": "string", "example": "0U0RxuLEeCp9gUUh80rrUI1vQis3q4wo" },
              "is_vehicle_document_uploaded": { "type": "boolean", "example": false },
              "service_type": { "type": "string", "nullable": true, "example": null },
              "admintypeid": { "type": "string", "nullable": true, "example": null },
              "is_available": { "type": "integer", "example": 1 },
              "is_active": { "type": "integer", "example": 0 },
              "is_partner_approved_by_admin": { "type": "integer", "example": 1 },
              "picture": { "type": "string", "example": "" }
            }
          }
        }
      }
    }
  }
}

```
