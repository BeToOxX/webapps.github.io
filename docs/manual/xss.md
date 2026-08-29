# 5. Stored XSS

## Objetivo

Comprobar si el módulo de reseñas ejecuta contenido proporcionado por usuarios como HTML/JavaScript.

## Prueba controlada

En el campo de reseña:

```html
<script>alert('XSS - ByteVault')</script>
```

En la versión vulnerable el navegador muestra una ventana de alerta.

Al volver a cargar la sección de reseñas, el código vuelve a ejecutarse porque quedó almacenado en la base de datos.

## Causa

La plantilla vulnerable utiliza:

```html
{{ r.body|safe }}
```

`safe` evita el escape automático.

## Riesgo

<span class="risk-high">ALTO</span>

Un XSS puede ejecutar acciones dentro del navegador de otro usuario bajo el contexto del sitio.

## Corrección

La versión segura utiliza:

```html
{{ r.body }}
```

Jinja escapa el contenido y lo trata como texto.

## Limpiar la prueba

Antes de una exposición puede restablecerse la base:

```bash
cd ~/web_security_lab_v2/vulnerable_app
source .venv/bin/activate
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```
