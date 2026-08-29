# Resultados, recomendaciones y conclusiones

## 21. Comparación de resultados

| Control / Vulnerabilidad | Vulnerable | Segura |
|---|---|---|
| SQL Injection | ❌ Vulnerable | ✅ Corregida |
| Stored XSS | ❌ Vulnerable | ✅ Corregida |
| IDOR en perfiles | ❌ Vulnerable | ✅ Corregida |
| IDOR en pedidos | ❌ Vulnerable | ✅ Corregida |
| Tokens Anti-CSRF | ❌ Ausentes | ✅ Implementados |
| Contraseñas | ❌ Texto plano | ✅ Hash |
| Consultas SQL | ❌ Concatenadas | ✅ Parametrizadas |
| CSP | ❌ Ausente | ✅ Implementada |
| X-Content-Type-Options | ❌ Ausente | ✅ Implementado |
| Anti-Clickjacking | ❌ Ausente | ✅ Implementado |
| Debug | ❌ Activado | ✅ Desactivado |
| Control de autorización | ❌ Insuficiente | ✅ Implementado |

---

## 22. Hallazgos principales

### Riesgo alto

1. SQL Injection.
2. Stored Cross-Site Scripting.
3. IDOR / Broken Access Control en perfiles.
4. IDOR / Broken Access Control en pedidos.

### Riesgo medio

1. Ausencia de protección Anti-CSRF.
2. Ausencia de Content Security Policy.
3. Falta de protección Anti-Clickjacking.

### Riesgo bajo / informativo

1. Divulgación de versiones de software.
2. Cabeceras HTTP adicionales ausentes.
3. Información de autenticación y sesión identificada.

---

## 23. Recomendaciones

- Utilizar consultas parametrizadas.
- Nunca almacenar contraseñas en texto plano.
- Aplicar autorización sobre cada recurso solicitado.
- Implementar tokens Anti-CSRF.
- Escapar contenido generado por usuarios.
- Utilizar CSP restrictiva.
- Configurar cabeceras HTTP de seguridad.
- Evitar divulgar versiones innecesarias.
- Deshabilitar debug en producción.
- Incorporar pruebas de seguridad al ciclo de desarrollo.
- Utilizar análisis automatizado como complemento de pruebas manuales.

---

## 24. Conclusiones

La práctica permitió comprobar que una aplicación funcional no necesariamente es segura. La versión vulnerable de VaultStore presentaba fallas relacionadas con validación de entradas, autenticación, autorización, almacenamiento de contraseñas y configuración HTTP.

WhatWeb, Nikto, Nmap y OWASP ZAP facilitaron la identificación de tecnologías, servicios y vulnerabilidades. Sin embargo, las pruebas manuales fueron fundamentales para confirmar SQL Injection, Stored XSS e IDOR.

Después de implementar controles de seguridad, las pruebas realizadas contra la segunda versión demostraron una reducción significativa de vulnerabilidades. Esto evidencia la importancia de integrar seguridad durante el desarrollo de aplicaciones.

---

## 25. Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| Kali Linux | Entorno de auditoría |
| WSL 2 | Ejecución de Kali Linux en Windows |
| Python | Ejecución de las aplicaciones |
| Flask | Framework web |
| SQLite | Base de datos |
| WhatWeb | Reconocimiento tecnológico |
| Nikto | Evaluación de configuración HTTP |
| Nmap | Identificación de puertos y servicios |
| OWASP ZAP | Análisis automatizado |
| GitHub Pages | Publicación del manual |

---

## 26. Referencias

- OWASP Foundation. *OWASP Web Security Testing Guide*.
- OWASP Foundation. *OWASP Top 10*.
- OWASP ZAP. *Zed Attack Proxy Documentation*.
- Kali Linux. *Kali Tools Documentation*.
- Nmap Project. *Nmap Reference Guide*.
- Flask Documentation. *Flask Web Development Framework*.

---

Este laboratorio fue diseñado con fines académicos para la asignatura **Seguridad y Auditoría de Sistemas** y se ejecuta dentro de un entorno local controlado.
