# Pruebas manuales de seguridad

Las siguientes pruebas se realizan únicamente contra **VaultStore Vulnerable** dentro del laboratorio local.

---

## 10. Prueba de SQL Injection

### 10.1 Comprobar el inicio de sesión normal

Primero se verifica que credenciales incorrectas sean rechazadas:

```text
Usuario: prueba
Contraseña: prueba
```

La aplicación no debería permitir el acceso.

### 10.2 Introducir el payload de laboratorio

En el campo **Usuario** introducir:

```text
' OR '1'='1' -- 
```

En el campo **Contraseña** introducir:

```text
hola
```

Luego presionar el botón para iniciar sesión.

### 10.3 Resultado

En la versión vulnerable la aplicación permite iniciar sesión sin conocer una contraseña válida.

Esto ocurre porque la entrada proporcionada altera la lógica de una consulta SQL construida de forma insegura.

Ejemplo conceptual vulnerable:

```python
sql = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
```

**Riesgo:** Alto.

### 10.4 Mitigación

La versión segura debe utilizar:

- Consultas parametrizadas.
- Hashing de contraseñas.
- Validación de entradas.
- Manejo adecuado de errores.

---

## 11. Prueba de Stored Cross-Site Scripting

### 11.1 Ingresar a la sección de reseñas

Dentro de VaultStore Vulnerable, abrir la sección donde se publican o almacenan reseñas.

### 11.2 Introducir el payload de laboratorio

En el campo de texto de la reseña introducir:

```html
<script>alert('XSS - VaultStore')</script>
```

Guardar o publicar la reseña.

### 11.3 Volver a cargar la sección

Actualizar la página o ingresar nuevamente a la sección de reseñas.

### 11.4 Resultado

En la versión vulnerable el contenido queda almacenado en la base de datos y el navegador ejecuta el JavaScript al mostrar nuevamente la reseña.

**Riesgo:** Alto.

### 11.5 Mitigación

- Escape de salida.
- Validación y sanitización cuando corresponda.
- Uso seguro de plantillas.
- Content Security Policy restrictiva.

---

## 12. Prueba de IDOR en perfiles

### 12.1 Abrir el perfil actual

La aplicación vulnerable utiliza una ruta similar a:

```text
/profile/1
```

### 12.2 Modificar el identificador

Cambiar manualmente la URL por:

```text
/profile/2
```

Después probar:

```text
/profile/3
```

### 12.3 Resultado

La aplicación vulnerable muestra información perteneciente a otros usuarios sin verificar correctamente que el recurso solicitado corresponda al usuario autenticado.

**Riesgo:** Alto.

### 12.4 Mitigación

La aplicación debe verificar la autorización del lado del servidor en cada solicitud.

---

## 13. Prueba de IDOR en pedidos

### 13.1 Probar identificadores de pedidos

Acceder directamente a:

```text
/order/3
```

Después:

```text
/order/4
```

### 13.2 Resultado

La versión vulnerable permite visualizar pedidos pertenecientes a otros usuarios.

**Riesgo:** Alto.

### 13.3 Mitigación

El servidor debe comprobar que el pedido solicitado pertenezca al usuario autenticado antes de devolver la información.
