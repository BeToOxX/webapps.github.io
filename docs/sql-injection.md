# SQL Injection

## ¿Qué es SQL Injection?

**SQL Injection**, también denominado **SQLi**, es una vulnerabilidad que puede aparecer cuando una aplicación incorpora directamente datos proporcionados por el usuario dentro de una consulta SQL.

Esto puede provocar que la base de datos interprete parte de la entrada como instrucciones SQL.

---

## Ejemplo conceptual

Una aplicación podría construir una consulta de esta manera:

```python
query = "SELECT * FROM users WHERE username = '" + username + "'"
```

El problema consiste en concatenar directamente información proporcionada por el usuario.

---

## Riesgos

Una vulnerabilidad SQL Injection puede provocar:

- Acceso no autorizado.
- Consulta de información sensible.
- Modificación de información.
- Eliminación de registros.
- Alteración de la lógica de autenticación.
- Compromiso de la base de datos.

---

## Prueba en VaultStore Vulnerable

El laboratorio permite analizar el comportamiento de una funcionalidad que utiliza una consulta construida de manera insegura.

Una entrada utilizada únicamente dentro del entorno de laboratorio puede ser:

```text
' OR '1'='1
```

La finalidad es observar cómo una consulta construida incorrectamente puede modificar su comportamiento lógico.

---

## Mitigación

Una de las principales medidas para prevenir SQL Injection consiste en utilizar consultas parametrizadas.

Ejemplo:

```python
cursor.execute(
    "SELECT * FROM users WHERE username = ?",
    (username,)
)
```

En este caso, el valor proporcionado por el usuario es tratado como un dato y no como parte de la instrucción SQL.

---

## Buenas prácticas

- Utilizar consultas parametrizadas.
- Evitar concatenar entradas del usuario.
- Validar los datos recibidos.
- Utilizar cuentas de base de datos con privilegios mínimos.
- No mostrar errores internos de la base de datos.
- Mantener actualizados los componentes utilizados por la aplicación.
