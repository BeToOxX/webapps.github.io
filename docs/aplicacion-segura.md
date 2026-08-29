# Aplicación Segura

## VaultStore Secure

Después de identificar las vulnerabilidades presentes en VaultStore Vulnerable, se analizan mecanismos para desarrollar una versión más segura de la aplicación.

La finalidad no consiste únicamente en encontrar vulnerabilidades, sino en comprender cómo pueden prevenirse.

---

## Protección contra SQL Injection

La versión segura debe utilizar consultas parametrizadas.

Ejemplo:

```python
cursor.execute(
    "SELECT * FROM products WHERE id = ?",
    (product_id,)
)
```

De esta forma, los valores son procesados como datos.

---

## Protección contra XSS

La información ingresada por los usuarios no debe representarse directamente como HTML ejecutable.

Debe utilizarse:

- Escape de contenido.
- Sanitización cuando sea necesaria.
- Plantillas con escape automático.
- Content Security Policy.
- Validación de entradas.

---

## Protección contra IDOR

Cada recurso debe comprobarse contra el usuario autenticado.

Ejemplo:

```python
resource = get_resource(resource_id)

if resource.owner_id != current_user.id:
    abort(403)
```

Modificar un identificador no debería proporcionar acceso automáticamente a otro recurso.

---

## Principio de mínimo privilegio

Cada usuario, servicio o componente debe disponer únicamente de los permisos necesarios para realizar sus funciones.

Esto reduce el impacto potencial de una vulnerabilidad.

---

## Manejo de errores

La aplicación no debería mostrar información interna como:

- Consultas SQL.
- Rutas del sistema.
- Stack traces.
- Contraseñas.
- Variables internas.
- Información sensible de configuración.

Los errores deben ser registrados internamente y mostrar al usuario únicamente información apropiada.

---

## Seguridad por capas

Una aplicación segura no depende de una única medida de protección.

Es recomendable implementar múltiples controles:

1. Validación de entradas.
2. Autenticación.
3. Autorización.
4. Gestión de sesiones.
5. Protección de la base de datos.
6. Encabezados de seguridad.
7. Registro de eventos.
8. Monitoreo.
9. Actualización de componentes.
