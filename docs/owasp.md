# OWASP Top 10

## ¿Qué es OWASP?

**OWASP** significa **Open Worldwide Application Security Project**.

Es una organización internacional enfocada en mejorar la seguridad del software mediante proyectos, documentación, herramientas y recursos educativos de acceso público.

Uno de sus proyectos más conocidos es **OWASP Top 10**.

---

## ¿Qué es OWASP Top 10?

OWASP Top 10 presenta una clasificación de riesgos importantes relacionados con la seguridad de aplicaciones web.

Su propósito es ayudar a desarrolladores, auditores, administradores y profesionales de seguridad a comprender los principales problemas que pueden afectar una aplicación.

---

## Importancia

OWASP Top 10 permite:

- Identificar riesgos frecuentes.
- Mejorar las prácticas de programación.
- Establecer controles de seguridad.
- Apoyar procesos de auditoría.
- Capacitar a desarrolladores.
- Crear aplicaciones más seguras.

---

## Relación con VaultStore

Dentro del laboratorio se estudian diferentes problemas relacionados con riesgos reconocidos por OWASP.

### Injection

Los ataques de inyección ocurren cuando una aplicación interpreta información proporcionada por un usuario como parte de una instrucción o consulta.

Un ejemplo es:

**SQL Injection**

---

### Broken Access Control

Se produce cuando una aplicación no controla correctamente los recursos a los que puede acceder un usuario.

Un ejemplo estudiado durante el laboratorio es:

**IDOR — Insecure Direct Object Reference**

---

### Cross-Site Scripting

XSS permite introducir contenido que posteriormente puede ser interpretado por el navegador de otro usuario.

Dentro de VaultStore se estudia específicamente:

**Stored XSS**

---

## Importancia para el desarrollo

Conocer los riesgos definidos por OWASP permite incorporar controles de seguridad desde las primeras etapas del desarrollo de software.

La seguridad debe considerarse como una característica fundamental del sistema y no únicamente como una etapa adicional después de finalizar el desarrollo.
