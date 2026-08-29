# Preparación del laboratorio

## 4. Preparación de Kali Linux en WSL

### 4.1 Iniciar Kali Linux

Desde PowerShell o CMD:

```powershell
wsl -d kali-linux
```

Verificar la distribución:

```bash
cat /etc/os-release
```

### 4.2 Actualizar repositorios

```bash
sudo apt update
```

### 4.3 Instalar Python y utilidades

```bash
sudo apt install -y python3 python3-venv python3-pip unzip
```

Verificar:

```bash
python3 --version
```

Durante la práctica se utilizó:

```text
Python 3.13.12
```

### 4.4 Instalar herramientas de auditoría

```bash
sudo apt install -y whatweb nikto nmap
```

---

## 5. Preparación del laboratorio VaultStore

El archivo del laboratorio debe llamarse:

```text
vaultstore_web_security_lab_v2.zip
```

Acceder a la carpeta Descargas de Windows desde Kali:

```bash
cd /mnt/c/Users/nebuR/Downloads
```

Verificar que el archivo se encuentre en la carpeta:

```bash
ls
```

Copiar el archivo al directorio personal de Kali:

```bash
cp vaultstore_web_security_lab_v2.zip ~/
```

Ir al directorio personal:

```bash
cd ~
```

Descomprimir:

```bash
unzip vaultstore_web_security_lab_v2.zip
```

La estructura esperada es:

```text
web_security_lab_v2/
├── vulnerable_app/
└── secure_app/
```

---

## 6. Ejecutar VaultStore Vulnerable

### 6.1 Acceder al proyecto

```bash
cd ~/web_security_lab_v2/vulnerable_app
```

### 6.2 Crear el entorno virtual

```bash
python3 -m venv .venv
```

### 6.3 Activar el entorno virtual

```bash
source .venv/bin/activate
```

Cuando el entorno esté activo, normalmente aparecerá `(.venv)` al inicio de la terminal.

### 6.4 Instalar dependencias

```bash
pip install -r requirements.txt
```

### 6.5 Inicializar la base de datos

```bash
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

El resultado esperado es:

```text
Base de datos reiniciada correctamente
```

### 6.6 Ejecutar la aplicación vulnerable

```bash
python -m flask --app app run --host=0.0.0.0 --port=5000
```

### 6.7 Obtener la dirección IP de Kali/WSL

En otra terminal:

```bash
hostname -I
```

Durante la práctica se obtuvo:

```text
172.22.136.16
```

La dirección puede cambiar en otro equipo o al reiniciar WSL. Se debe utilizar la IP que devuelva `hostname -I`.

Ejemplo de acceso:

```text
http://172.22.136.16:5000
```

### 6.8 Credenciales de la versión vulnerable

```text
Usuario: admin
Contraseña: admin123
```

Al abrir la dirección en el navegador debe mostrarse **VaultStore Vulnerable**.
