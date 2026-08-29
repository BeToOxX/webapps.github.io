# Reconocimiento con WhatWeb, Nikto y Nmap

Antes de realizar las pruebas manuales se hace un reconocimiento inicial de la aplicación vulnerable.

La URL utilizada durante la práctica fue:

```text
http://172.22.136.16:5000
```

Si la IP de WSL es distinta, debe sustituirse por la obtenida con:

```bash
hostname -I
```

---

## 7. Reconocimiento con WhatWeb

Ejecutar:

```bash
whatweb http://172.22.136.16:5000
```

Durante la práctica se identificaron elementos como:

```text
HTTP 200 OK
HTML5
Werkzeug 3.1.3
Python 3.13.12
VaultStore
```

### ¿Qué se comprueba?

WhatWeb permite identificar tecnologías utilizadas por la aplicación y, en algunos casos, versiones de software expuestas.

La exposición innecesaria de versiones puede facilitar el reconocimiento técnico de un sistema.

---

## 8. Análisis con Nikto

Ejecutar:

```bash
nikto -h http://172.22.136.16:5000
```

Entre los hallazgos analizados se encuentran:

- Ausencia de `Content-Security-Policy`.
- Ausencia de `Referrer-Policy`.
- Ausencia de `X-Content-Type-Options`.
- Ausencia de `Permissions-Policy`.
- Ausencia de `Strict-Transport-Security`.
- Divulgación de versiones de Werkzeug y Python.

### ¿Qué significa?

Nikto analiza configuraciones comunes del servidor web y puede detectar cabeceras de seguridad faltantes, información expuesta y otras configuraciones que requieren revisión.

---

## 9. Análisis de puertos y servicios con Nmap

### 9.1 Escaneo general

```bash
nmap 172.22.136.16
```

### 9.2 Detección de versión en el puerto 5000

```bash
nmap -sV -p 5000 172.22.136.16
```

Resultado obtenido durante la práctica:

```text
PORT      STATE SERVICE VERSION
5000/tcp  open  http    Werkzeug httpd 3.1.3 (Python 3.13.12)
```

### ¿Qué se comprueba?

Nmap permite identificar puertos abiertos y servicios disponibles. En este caso confirma que la aplicación vulnerable está escuchando en el puerto `5000`.
