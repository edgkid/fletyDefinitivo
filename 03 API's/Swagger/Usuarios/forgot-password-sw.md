### Recuperar Contraseña

```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API - recuperar contraseña",
    "version": "1.0.0",
    "description": "API para gestionar procesos de autenticación, solicitud de restablecimiento de contraseña."
  },
  "paths": {
    "/forgotpassword": {
      "post": {
        "summary": "Solicitar Restablecimiento de Contraseña",
        "description": "Inicia el proceso de 'Olvidé mi contraseña'. Envía un enlace o código de restablecimiento al correo electrónico proporcionado, dependiendo del tipo de usuario.",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "email": {
                    "type": "string",
                    "format": "email",
                    "description": "Correo electrónico del usuario que solicita el restablecimiento."
                  },
                  "type": {
                    "type": "integer",
                    "description": "Tipo de usuario o plataforma (Ej: 1 = Usuario regular, 2 = Administrador, etc.).",
                    "example": 1
                  }
                },
                "required": [
                  "email",
                  "type"
                ],
                "example": {
                  "email": "android@user.com",
                  "type": 1
                }
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Proceso iniciado exitosamente. Se ha enviado el enlace/código de restablecimiento al correo.",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "success": {
                      "type": "boolean",
                      "description": "Indica si la operación fue exitosa."
                    },
                    "message": {
                      "type": "string",
                      "description": "Código de respuesta que indica éxito. (Ej: '77')"
                    }
                  },
                  "example": {
                    "success": true,
                    "message": "77"
                  }
                }
              }
            }
          },
          "400": {
            "description": "Solicitud inválida (ej. formato de email incorrecto o parámetros faltantes)."
          },
          "404": {
            "description": "Usuario no encontrado para el email proporcionado."
          }
        }
      }
    }
  }
}


```
