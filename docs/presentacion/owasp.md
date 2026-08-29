# OWASP Top 10:2025

El **OWASP Top 10** es un documento de concientización ampliamente utilizado para representar riesgos críticos de seguridad en aplicaciones web. La versión vigente es **OWASP Top 10:2025**.

## Las 10 categorías

| Código | Riesgo |
|---|---|
| A01:2025 | Pérdida de Control de Acceso |
| A02:2025 | Configuración de Seguridad Incorrecta |
| A03:2025 | Fallas en la Cadena de Suministro de Software |
| A04:2025 | Fallas Criptográficas |
| A05:2025 | Inyección |
| A06:2025 | Diseño Inseguro |
| A07:2025 | Fallas de Autenticación |
| A08:2025 | Fallas en la Integridad del Software o de los Datos |
| A09:2025 | Fallas en el Registro, Alerta y Monitoreo de Seguridad |
| A10:2025 | Manejo Inadecuado de Condiciones Excepcionales |

## Categorías relacionadas con ByteVault

### A01: Pérdida de Control de Acceso

Se relaciona directamente con los casos de **IDOR** del laboratorio.

En la versión vulnerable un usuario puede modificar un identificador y consultar recursos de otro usuario.

### A02: Configuración de Seguridad Incorrecta

Relacionada con:

- falta de CSP;
- falta de `X-Content-Type-Options`;
- falta de políticas HTTP adicionales;
- modo debug activo;
- divulgación de información tecnológica.

### A05: Inyección

Relacionada con:

- **SQL Injection**;
- **Cross-Site Scripting (XSS)**.

La edición 2025 de OWASP incluye ambos tipos de problema dentro de la categoría de inyección.

### A07: Fallas de Autenticación

El bypass del formulario de login demuestra cómo un fallo de inyección puede terminar comprometiendo el proceso de autenticación.

## Mapeo de la práctica

| Hallazgo | OWASP 2025 |
|---|---|
| IDOR perfiles/pedidos | A01 Pérdida de Control de Acceso |
| Cabeceras ausentes / debug | A02 Configuración Incorrecta |
| SQL Injection | A05 Inyección |
| Stored XSS | A05 Inyección |
| Bypass de login | A05 + impacto en A07 |

!!! tip "Para la exposición"
    No es necesario memorizar las diez categorías. Lo importante es explicar que OWASP permite clasificar los hallazgos dentro de un marco reconocido de seguridad.

## Fuente oficial

[OWASP Top 10:2025](https://owasp.org/Top10/2025/){ target="_blank" }
