# OWASP ZAP

## ¿Qué es OWASP ZAP?

**OWASP ZAP** significa **OWASP Zed Attack Proxy**.

Es una herramienta de código abierto diseñada para analizar la seguridad de aplicaciones web.

Puede actuar como intermediario entre el navegador y el servidor, permitiendo observar las solicitudes y respuestas HTTP.

---

## Funciones principales

OWASP ZAP permite:

- Interceptar solicitudes.
- Analizar respuestas.
- Ejecutar análisis pasivos.
- Realizar escaneos automatizados.
- Examinar encabezados HTTP.
- Identificar configuraciones inseguras.
- Analizar cookies.
- Detectar posibles vulnerabilidades.

---

## Uso en el laboratorio

La aplicación VaultStore puede ejecutarse localmente y posteriormente analizarse desde ZAP.

Ejemplo:

```text
http://127.0.0.1:5000
```

Desde OWASP ZAP se puede navegar por la aplicación y observar los resultados encontrados.

---

## Alertas

ZAP clasifica los resultados de acuerdo con diferentes niveles de riesgo.

Por ejemplo:

- Informativo.
- Bajo.
- Medio.
- Alto.

No todas las alertas representan automáticamente una vulnerabilidad explotable.

Cada resultado debe ser analizado para determinar:

- El contexto.
- La funcionalidad afectada.
- El impacto.
- La probabilidad.
- Las medidas de mitigación.

---

## Análisis pasivo

Durante el análisis pasivo, ZAP examina las solicitudes y respuestas sin modificar activamente el comportamiento de la aplicación.

Puede identificar aspectos como:

- Encabezados faltantes.
- Cookies inseguras.
- Información expuesta.
- Configuraciones HTTP.

---

## Importancia

Las herramientas automatizadas son útiles para apoyar una auditoría, pero no sustituyen completamente el análisis manual.

El resultado debe ser interpretado por una persona que comprenda el funcionamiento de la aplicación.
