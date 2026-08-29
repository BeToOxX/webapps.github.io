# 4. SQL Injection

## Objetivo

Comprobar si el formulario de autenticación construye consultas SQL de forma insegura.

## Paso 1: intento normal incorrecto

En el login:

```text
Usuario: prueba
Contraseña: prueba
```

Resultado:

```text
Credenciales inválidas
```

## Paso 2: prueba controlada

Únicamente contra ByteVault local:

```text
Usuario: ' OR '1'='1' -- 
Contraseña: hola
```

En la versión vulnerable el acceso puede ser aceptado sin conocer una contraseña válida.

## ¿Por qué ocurre?

La aplicación vulnerable utiliza conceptualmente una consulta como:

```python
sql = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
```

La entrada del usuario pasa a formar parte del código SQL.

## Riesgo

<span class="risk-high">ALTO</span>

Una inyección puede provocar bypass de autenticación, manipulación de datos o acceso a información.

## Corrección

La versión segura utiliza parámetros:

```python
c.execute(
    "SELECT * FROM users WHERE username=?",
    (username,)
)
```

El valor pasa a tratarse como **dato**, no como código SQL.
