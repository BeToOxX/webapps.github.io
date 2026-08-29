# Stored XSS

## ¿Qué es XSS?

**XSS** significa **Cross-Site Scripting**.

Es una vulnerabilidad que ocurre cuando una aplicación permite que contenido controlado por un usuario sea interpretado como código por el navegador.

---

## Stored XSS

En **Stored XSS**, el contenido introducido por un usuario queda almacenado de forma permanente en la aplicación.

Puede almacenarse, por ejemplo, en:

- Una base de datos.
- Comentarios.
- Perfiles.
- Publicaciones.
- Descripciones.
- Formularios.

Cuando otro usuario consulta posteriormente esa información, el navegador podría interpretar el contenido como código.

---

## Prueba en VaultStore Vulnerable

Dentro del laboratorio puede utilizarse una entrada sencilla para demostrar el comportamiento:

```html
<script>alert('VaultStore')</script>
```

Si la aplicación almacena el contenido sin aplicar controles y posteriormente lo representa directamente en HTML, el navegador puede ejecutar el código.

---

## Riesgos

Stored XSS puede utilizarse para:

- Modificar el contenido visible de una página.
- Ejecutar JavaScript dentro del navegador.
- Manipular elementos de la interfaz.
- Realizar acciones utilizando el contexto del usuario.
- Comprometer información disponible dentro de la sesión.

---

## Mitigación

La principal protección consiste en codificar correctamente la información antes de representarla dentro de una página HTML.

Los frameworks modernos suelen proporcionar mecanismos de escape automático.

También pueden utilizarse controles adicionales como:

- Validación de entradas.
- Sanitización.
- Content Security Policy.
- Cookies con atributos de seguridad.
- Uso adecuado de plantillas.
- Evitar insertar contenido directamente mediante `innerHTML`.

---

## Aplicación segura

En **VaultStore Secure**, los valores proporcionados por el usuario deben ser tratados como contenido y no como código ejecutable.

Por lo tanto, una entrada como:

```html
<script>alert('VaultStore')</script>
```

debería visualizarse como texto o ser procesada de manera segura, en lugar de ejecutarse.
