# 1. Preparar Kali en WSL

## Iniciar Kali

Desde Warp, PowerShell o Windows Terminal:

```powershell
wsl -d kali-linux
```

## Actualizar repositorios

```bash
sudo apt update
```

## Instalar Python y utilidades

```bash
sudo apt install -y python3 python3-venv python3-pip unzip
```

Verificar:

```bash
python3 --version
```

En el laboratorio se utilizó:

```text
Python 3.13.12
```

## Instalar herramientas

```bash
sudo apt install -y whatweb nikto nmap
```

## Copiar el ZIP desde Windows

Si el archivo se encuentra en:

```text
C:\Users\nebuR\Downloads
```

desde Kali:

```bash
cd /mnt/c/Users/nebuR/Downloads
ls
```

Copiar:

```bash
cp bytevault_web_security_lab_v2.zip ~/
```

Ir al home:

```bash
cd ~
```

Descomprimir:

```bash
unzip bytevault_web_security_lab_v2.zip
```

Verificar:

```bash
ls
```

Debe existir:

```text
web_security_lab_v2
```

## Obtener la IP de WSL

```bash
hostname -I
```

Ejemplo utilizado en la práctica:

```text
172.22.136.16
```

!!! note
    La IP puede cambiar después de reiniciar WSL. Si una URL deja de funcionar, ejecuta nuevamente `hostname -I`.
