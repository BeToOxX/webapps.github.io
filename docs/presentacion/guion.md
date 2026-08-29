# Guion de exposición

Una forma sencilla de presentar el tema es seguir este orden.

## 1. Introducción

> Una aplicación web no solo muestra información; normalmente procesa usuarios, sesiones, formularios y bases de datos. Por eso una falla puede comprometer información o permitir operaciones que el usuario no debería realizar.

## 2. ¿Qué es una Web App?

Explicar brevemente:

```text
Navegador → Servidor → Aplicación → Base de datos
```

## 3. ¿Qué busca proteger la seguridad?

Mencionar:

- confidencialidad;
- integridad;
- disponibilidad;
- autenticación;
- autorización.

## 4. OWASP Top 10

Explicar que OWASP proporciona una referencia para clasificar riesgos y mencionar especialmente:

- A01 Pérdida de Control de Acceso;
- A02 Configuración Incorrecta;
- A05 Inyección;
- A07 Fallas de Autenticación.

## 5. Presentar ByteVault

Explicar que existen dos aplicaciones equivalentes:

```text
:5000 → vulnerable
:5001 → segura
```

## 6. Reconocimiento

Demostrar:

```bash
whatweb
nikto
nmap
```

## 7. Ataques controlados

Demostrar en este orden:

1. SQL Injection.
2. Stored XSS.
3. IDOR.
4. OWASP ZAP.

## 8. Aplicación segura

Repetir los mismos intentos y mostrar que los controles evitan los ataques.

## 9. Conclusión

> Las herramientas automatizadas ayudan a encontrar problemas, pero la seguridad real depende de diseñar controles correctos dentro de la aplicación y validarlos mediante pruebas.
