# 2. ByteVault vulnerable

## Entrar al proyecto

```bash
cd ~/web_security_lab_v2/vulnerable_app
```

## Crear entorno virtual

```bash
python3 -m venv .venv
```

Activarlo:

```bash
source .venv/bin/activate
```

La terminal mostrará:

```text
(.venv)
```

## Instalar dependencias

```bash
pip install -r requirements.txt
```

## Inicializar la base de datos

```bash
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

Esto crea/restablece:

```text
bytevault.db
```

## Levantar la aplicación

```bash
python -m flask --app app run --host=0.0.0.0 --port=5000
```

Abrir desde Windows:

```text
http://IP_DE_WSL:5000
```

Ejemplo:

```text
http://172.22.136.16:5000
```

## Credenciales

```text
Usuario: admin
Contraseña: admin123
```

## Restablecer antes de una demostración

Si se almacenó un payload XSS o se modificó información:

```bash
cd ~/web_security_lab_v2/vulnerable_app
source .venv/bin/activate
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

Después reinicia Flask si es necesario.
