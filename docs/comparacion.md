# Comparación

## VaultStore Vulnerable vs. VaultStore Secure

El laboratorio permite comparar directamente una implementación vulnerable con una implementación que incorpora controles de seguridad.

| Característica | VaultStore Vulnerable | VaultStore Secure |
|---|---|---|
| Consultas SQL | Construcción insegura | Consultas parametrizadas |
| Validación de entradas | Limitada | Validación implementada |
| Protección XSS | Inadecuada | Escape y controles de contenido |
| Autorización | Controles insuficientes | Validación del usuario y recurso |
| Manejo de errores | Puede exponer información | Mensajes controlados |
| Seguridad | Vulnerable | Controles de seguridad |
| Objetivo | Demostración académica | Demostración de mitigaciones |

---

## SQL Injection

### Vulnerable

Los datos pueden incorporarse directamente dentro de una consulta SQL.

### Seguro

Los valores se transmiten mediante parámetros.

---

## Stored XSS

### Vulnerable

El contenido introducido por el usuario puede almacenarse y posteriormente representarse sin controles adecuados.

### Seguro

El contenido es tratado como información y no como código ejecutable.

---

## IDOR

### Vulnerable

La aplicación confía en el identificador recibido.

### Seguro

El servidor comprueba que el usuario tenga autorización para acceder al recurso.

---

## Resultado

La comparación demuestra que pequeñas decisiones durante el desarrollo pueden tener una influencia considerable en la seguridad de una aplicación.

La validación, parametrización y autorización deben implementarse desde el diseño del sistema.
