# Recomendaciones

## Desarrollo

- utilizar consultas SQL parametrizadas;
- validar entradas según su contexto;
- escapar siempre la salida generada por usuarios;
- evitar mecanismos que deshabiliten el escape automático;
- utilizar hashing seguro para contraseñas.

## Autenticación y autorización

- comprobar autorización en cada endpoint;
- no confiar únicamente en elementos ocultos de la interfaz;
- asociar los recursos al usuario autenticado;
- limitar intentos de autenticación.

## HTTP y navegador

- implementar CSP;
- configurar `X-Content-Type-Options`;
- restringir framing/clickjacking;
- definir `Referrer-Policy`;
- revisar `Permissions-Policy`;
- utilizar HTTPS en despliegues reales.

## Operación

- deshabilitar debug en producción;
- minimizar información de versión;
- registrar eventos relevantes de seguridad;
- mantener dependencias actualizadas;
- realizar análisis automatizado y manual periódicamente.
