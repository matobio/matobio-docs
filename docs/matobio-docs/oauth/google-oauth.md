---
sidebar_position: 1
---

# Google OAuth

Las APIs de Google usan el protocolo OAuth 2.0 para autenticación y autorización. Google admite escenarios comunes de OAuth 2.0, como los de servidor web, aplicaciones instaladas y aplicaciones del lado del cliente.

En primer lugar, se obtienen las credenciales de cliente de OAuth 2.0 desde la Google API Console. Luego, su aplicación cliente solicita un token de acceso del Servidor de Autorización de Google, extrae un token de la respuesta y envía el token a la API de Google a la que desea accede.

Para ver las aplicaciones que tienen acceso a tu cuenta se pueden consultar desde la url https://myaccount.google.com/u/1/permissions?pageId=none. Sólo puede haber acceso desde un servidor de elastic.