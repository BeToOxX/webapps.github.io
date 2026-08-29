# Aplicación segura y repetición de pruebas

## 15. Ejecutar VaultStore Secure

La versión segura se ejecuta en un puerto diferente para poder compararla con la versión vulnerable.

### 15.1 Acceder al proyecto

```bash
cd ~/web_security_lab_v2/secure_app
```

### 15.2 Crear el entorno virtual

```bash
python3 -m venv .venv
```

### 15.3 Activar el entorno virtual

```bash
source .venv/bin/activate
```

### 15.4 Instalar dependencias

```bash
pip install -r requirements.txt
```

### 15.5 Inicializar la base de datos

```bash
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

Resultado esperado:

```text
Base de datos reiniciada correctamente
```

### 15.6 Ejecutar la aplicación segura

```bash
python -m flask --app app run --host=0.0.0.0 --port=5001
```

Ejemplo de URL:

```text
http://172.22.136.16:5001
```

### 15.7 Credenciales

```text
Usuario: admin
Contraseña: Cambiame123!
```

---

## 16. Controles implementados

VaultStore Secure incluye:

- Consultas SQL parametrizadas.
- Hashing de contraseñas.
- Escape automático de HTML.
- Protección Anti-CSRF.
- Verificación de autorización sobre perfiles y pedidos.
- `Content-Security-Policy`.
- `X-Content-Type-Options`.
- `X-Frame-Options`.
- `Referrer-Policy`.
- `Permissions-Policy`.
- Mejoras de sesión.
- Limitación básica de intentos.
- Debug deshabilitado.

---

## 17. Repetición de SQL Injection

En el formulario de inicio de sesión volver a introducir:

```text
Usuario: ' OR '1'='1' -- 
Contraseña: hola
```

Resultado esperado:

```text
Credenciales inválidas
```

La consulta parametrizada impide que la entrada modifique la lógica SQL.

---

## 18. Repetición de Stored XSS

En la sección de reseñas introducir nuevamente:

```html
<script>alert('XSS - VaultStore')</script>
```

### Resultado esperado

La versión segura no debe ejecutar JavaScript. El contenido debe ser tratado como texto o procesado de forma segura.

---

## 19. Repetición de IDOR

En la versión segura se debe intentar repetir la manipulación de identificadores utilizada anteriormente.

Ejemplos:

```text
/profile/2
/profile/3
/order/3
/order/4
```

### Resultado esperado

La aplicación debe impedir el acceso a recursos pertenecientes a otros usuarios.

El perfil debe obtenerse a partir de la sesión autenticada o debe comprobarse la propiedad del recurso.

Los pedidos individuales también deben verificar que el recurso corresponda al usuario autenticado.

---

## 20. OWASP ZAP contra VaultStore Secure

Para evitar mezclar los resultados con la versión vulnerable, iniciar una sesión separada en ZAP.

URL:

```text
http://172.22.136.16:5001
```

Realizar nuevamente el análisis.

### Resultado esperado

No deberían aparecer como explotables los problemas corregidos, entre ellos:

- SQL Injection.
- Stored XSS.
- Ausencia de Anti-CSRF.
- Falta de `X-Content-Type-Options`.
- Falta de protección Anti-Clickjacking.

Los hallazgos restantes pueden corresponder a recomendaciones adicionales de endurecimiento, configuración o divulgación tecnológica.
