# Conclusiones

La práctica demuestra que una aplicación puede ser funcional y, al mismo tiempo, contener fallas graves de seguridad.

Las herramientas de reconocimiento permitieron identificar tecnologías, servicios y configuraciones visibles. OWASP ZAP facilitó el análisis automatizado, mientras que las pruebas manuales permitieron confirmar el impacto de SQL Injection, Stored XSS e IDOR.

La comparación con ByteVault Secure demuestra que medidas relativamente concretas —consultas parametrizadas, autorización por recurso, escape HTML, CSRF, hashing y cabeceras de seguridad— cambian significativamente el comportamiento frente a los mismos ataques.

## Conclusión principal

> La seguridad de aplicaciones web debe integrarse desde el diseño y mantenerse durante todo el ciclo de vida del software; no debe considerarse únicamente una revisión al final del desarrollo.
