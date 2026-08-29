# 8. ByteVault segura

La versión segura mantiene las mismas funciones principales, pero modifica la forma en que procesa entradas, sesiones y permisos.

## Entrar al proyecto

```bash
cd ~/web_security_lab_v2/secure_app
```

## Crear y activar entorno

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## Instalar dependencias

```bash
pip install -r requirements.txt
```

## Inicializar base

```bash
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

## Levantar en el puerto 5001

```bash
python -m flask --app app run --host=0.0.0.0 --port=5001
```

Abrir:

```text
http://172.22.136.16:5001
```

## Credenciales

```text
Usuario: admin
Contraseña: Cambiame123!
```

## Controles implementados

- consultas SQL parametrizadas;
- hashing de contraseñas;
- escape HTML;
- token Anti-CSRF;
- autorización sobre perfiles y pedidos;
- Content Security Policy;
- `X-Content-Type-Options`;
- `X-Frame-Options`;
- `Referrer-Policy`;
- `Permissions-Policy`;
- cookies con controles adicionales;
- rate limit básico en login;
- debug deshabilitado.

## Repetir SQL Injection

```text
Usuario: ' OR '1'='1' -- 
Contraseña: hola
```

Resultado esperado:

```text
Credenciales inválidas
```

## Repetir XSS

```html
<script>alert('XSS - ByteVault')</script>
```

Resultado esperado: se muestra como texto y no se ejecuta.

## Repetir IDOR

La ruta de perfil segura depende de la sesión:

```text
/profile
```

Los pedidos verifican que el usuario autenticado sea el propietario.
