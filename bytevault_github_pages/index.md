---
layout: default
title: "Práctica de Seguridad en Aplicaciones Web"
---

# Práctica de Seguridad en Aplicaciones Web

## Seguridad y Auditoría de Sistemas

**Laboratorio:** ByteVault Web Security Lab  
**Entorno:** Windows + WSL 2 + Kali Linux  
**Aplicaciones evaluadas:** versión vulnerable y versión segura  
**Herramientas utilizadas:** WhatWeb, Nikto, Nmap y OWASP ZAP

---

## 1. Introducción

Las aplicaciones web forman parte de la infraestructura tecnológica utilizada por organizaciones, instituciones y usuarios para acceder a sistemas, servicios y datos mediante un navegador. Debido a que estas aplicaciones pueden procesar información sensible, autenticación de usuarios y operaciones internas, es necesario evaluar sus controles de seguridad con el fin de identificar vulnerabilidades que puedan comprometer la confidencialidad, integridad o disponibilidad de la información.

En esta práctica se construyeron y evaluaron dos versiones de una aplicación web denominada **ByteVault Store**. La primera versión fue desarrollada deliberadamente con vulnerabilidades para fines académicos, mientras que la segunda incorpora controles de seguridad para mitigar los riesgos identificados. Ambas aplicaciones fueron analizadas en un entorno local y controlado.

> **Importante:** Todas las pruebas descritas en este documento fueron realizadas exclusivamente contra aplicaciones propias dentro de un laboratorio local. No deben ejecutarse contra sistemas de terceros sin autorización.

---

## 2. Objetivos

### 2.1 Objetivo general

Evaluar la seguridad de una aplicación web mediante herramientas de análisis y pruebas controladas, identificando vulnerabilidades y comparando los resultados obtenidos entre una versión vulnerable y una versión con controles de seguridad implementados.

### 2.2 Objetivos específicos

- Preparar un entorno de laboratorio utilizando Kali Linux sobre WSL.
- Identificar tecnologías y servicios utilizados por la aplicación.
- Detectar configuraciones inseguras mediante herramientas automatizadas.
- Demostrar vulnerabilidades de forma controlada.
- Implementar y comprobar controles de mitigación.
- Comparar los resultados obtenidos entre ambas versiones.

---

# 3. Arquitectura del laboratorio

| Aplicación | Puerto | Descripción |
|---|---:|---|
| ByteVault Vulnerable | 5000 | Aplicación deliberadamente insegura |
| ByteVault Secure | 5001 | Aplicación con controles de seguridad |

```text
Windows
│
├── Navegador web
├── OWASP ZAP
│
└── WSL 2
    └── Kali Linux
        ├── Python / Flask
        ├── WhatWeb
        ├── Nikto
        ├── Nmap
        ├── ByteVault Vulnerable :5000
        └── ByteVault Secure     :5001
```

---

# 4. Preparación de Kali Linux en WSL

## 4.1 Iniciar Kali Linux

```powershell
wsl -d kali-linux
```

Verificar la distribución:

```bash
cat /etc/os-release
```

## 4.2 Actualizar repositorios

```bash
sudo apt update
```

## 4.3 Instalar Python y utilidades

```bash
sudo apt install -y python3 python3-venv python3-pip unzip
```

Verificar:

```bash
python3 --version
```

Durante la práctica:

```text
Python 3.13.12
```

## 4.4 Instalar herramientas de auditoría

```bash
sudo apt install -y whatweb nikto nmap
```

---

# 5. Preparación del laboratorio ByteVault

Archivo utilizado:

```text
bytevault_web_security_lab_v2.zip
```

Acceder a Descargas de Windows:

```bash
cd /mnt/c/Users/nebuR/Downloads
```

Verificar:

```bash
ls
```

Copiar a Kali:

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

Estructura:

```text
web_security_lab_v2/
├── vulnerable_app/
└── secure_app/
```

---

# 6. Aplicación vulnerable

## 6.1 Acceder al proyecto

```bash
cd ~/web_security_lab_v2/vulnerable_app
```

## 6.2 Crear y activar el entorno virtual

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 6.3 Instalar dependencias

```bash
pip install -r requirements.txt
```

## 6.4 Inicializar la base de datos

```bash
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

## 6.5 Ejecutar la aplicación

```bash
python -m flask --app app run --host=0.0.0.0 --port=5000
```

## 6.6 Obtener IP de WSL

```bash
hostname -I
```

Durante la práctica:

```text
172.22.136.16
```

URL:

```text
http://172.22.136.16:5000
```

Credenciales:

```text
Usuario: admin
Contraseña: admin123
```

### Evidencia

![Aplicación vulnerable](assets/img/01-bytevault-vulnerable.png)

---

# 7. Reconocimiento con WhatWeb

```bash
whatweb http://172.22.136.16:5000
```

Resultados identificados:

```text
HTTP 200 OK
HTML5
Werkzeug 3.1.3
Python 3.13.12
ByteVault Store
```

La aplicación expone información sobre tecnologías y versiones del servidor.

### Evidencia

![Resultado de WhatWeb](assets/img/02-whatweb.png)

---

# 8. Análisis con Nikto

```bash
nikto -h http://172.22.136.16:5000
```

Principales hallazgos:

- Ausencia de `Content-Security-Policy`.
- Ausencia de `Referrer-Policy`.
- Ausencia de `X-Content-Type-Options`.
- Ausencia de `Permissions-Policy`.
- Ausencia de `Strict-Transport-Security`.
- Divulgación de versiones de Werkzeug y Python.

### Evidencia

![Resultado de Nikto](assets/img/03-nikto.png)

---

# 9. Análisis de puertos y servicios con Nmap

Escaneo general:

```bash
nmap 172.22.136.16
```

Detección de versión:

```bash
nmap -sV -p 5000 172.22.136.16
```

Resultado:

```text
PORT      STATE SERVICE VERSION
5000/tcp  open  http    Werkzeug httpd 3.1.3 (Python 3.13.12)
```

### Evidencia

![Resultado de Nmap](assets/img/04-nmap.png)

---

# 10. Prueba de SQL Injection

Primero se comprobó que credenciales incorrectas fueran rechazadas:

```text
Usuario: prueba
Contraseña: prueba
```

Luego, exclusivamente en el laboratorio:

```text
Usuario: ' OR '1'='1' -- 
Contraseña: hola
```

La aplicación permitió iniciar sesión sin conocer una contraseña válida.

Ejemplo conceptual vulnerable:

```python
sql = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
```

**Riesgo:** Alto.

**Recomendación:** utilizar consultas parametrizadas y almacenar contraseñas mediante hashing.

### Evidencia

![SQL Injection](assets/img/05-sql-injection.png)

---

# 11. Prueba de Stored Cross-Site Scripting

En Reseñas se introdujo:

```html
<script>alert('XSS - ByteVault')</script>
```

El contenido fue almacenado en la base de datos y ejecutado al cargar nuevamente la sección.

**Riesgo:** Alto.

**Recomendación:** escape de salida, validación de entradas y CSP restrictiva.

### Evidencia

![Stored XSS](assets/img/06-stored-xss.png)

---

# 12. Prueba de IDOR en perfiles

Perfil original:

```text
/profile/1
```

Se modificó a:

```text
/profile/2
```

y:

```text
/profile/3
```

La aplicación mostró información perteneciente a otros usuarios sin verificar autorización.

**Riesgo:** Alto.

### Evidencia

![IDOR en perfiles](assets/img/07-idor-profile.png)

---

# 13. Prueba de IDOR en pedidos

Se accedió directamente a:

```text
/order/3
```

y:

```text
/order/4
```

La aplicación mostró pedidos de otros usuarios.

**Riesgo:** Alto.

### Evidencia

![IDOR en pedidos](assets/img/08-idor-orders.png)

---

# 14. Análisis automatizado con OWASP ZAP

En ZAP:

```text
Inicio Rápido
→ Escaneo Automatizado
```

URL:

```text
http://172.22.136.16:5000
```

Configuración:

```text
Política: Dev Standard
Spider tradicional: Activado
Modern Spider: Chrome
```

Hallazgos principales:

- Cross-Site Scripting.
- Inyección SQL.
- Ausencia de tokens Anti-CSRF.
- CSP no configurada.
- Falta de Anti-Clickjacking.
- Divulgación de información del servidor.
- Falta de `X-Content-Type-Options`.

### Evidencia

![Alertas de OWASP ZAP](assets/img/09-zap-vulnerable.png)

## 14.1 SQL Injection detectada por ZAP

ZAP identificó:

```text
GET /catalog (q)
POST /login (username)
POST /login (password)
```

### Evidencia

![SQL Injection detectada por ZAP](assets/img/10-zap-sqli.png)

---

# 15. Aplicación segura

## 15.1 Acceder al proyecto

```bash
cd ~/web_security_lab_v2/secure_app
```

## 15.2 Crear y activar entorno virtual

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 15.3 Instalar dependencias

```bash
pip install -r requirements.txt
```

## 15.4 Inicializar base de datos

```bash
python -c "from app import init_db; init_db(); print('Base de datos reiniciada correctamente')"
```

## 15.5 Ejecutar la aplicación segura

```bash
python -m flask --app app run --host=0.0.0.0 --port=5001
```

URL:

```text
http://172.22.136.16:5001
```

Credenciales:

```text
Usuario: admin
Contraseña: Cambiame123!
```

### Evidencia

![Aplicación segura](assets/img/11-bytevault-secure.png)

---

# 16. Controles implementados

La versión segura incluye:

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

# 17. Repetición de SQL Injection

Se intentó:

```text
Usuario: ' OR '1'='1' -- 
Contraseña: hola
```

Resultado esperado:

```text
Credenciales inválidas
```

La consulta parametrizada impide que la entrada modifique la lógica SQL.

### Evidencia

![SQL Injection bloqueada](assets/img/12-secure-sqli.png)

---

# 18. Repetición de XSS

Se ingresó nuevamente:

```html
<script>alert('XSS - ByteVault')</script>
```

La versión segura no ejecutó JavaScript y trató el contenido como texto.

### Evidencia

![XSS bloqueado](assets/img/13-secure-xss.png)

---

# 19. Repetición de IDOR

En la versión segura el perfil se obtiene a partir de la sesión autenticada.

Los pedidos individuales también verifican que el recurso corresponda al usuario autenticado.

Por lo tanto, ya no es posible consultar arbitrariamente perfiles o pedidos de terceros modificando un identificador en la URL.

---

# 20. OWASP ZAP contra la versión segura

Se utilizó una sesión separada en ZAP para evitar mezclar los resultados.

URL:

```text
http://172.22.136.16:5001
```

Dejaron de aparecer hallazgos graves como:

- SQL Injection.
- XSS explotable.
- Ausencia de Anti-CSRF.
- Falta de `X-Content-Type-Options`.
- Falta de protección Anti-Clickjacking.

Los hallazgos restantes correspondieron principalmente a recomendaciones adicionales de endurecimiento de CSP y divulgación tecnológica.

### Evidencia

![OWASP ZAP versión segura](assets/img/14-zap-secure.png)

---

# 21. Comparación de resultados

| Control / Vulnerabilidad | Vulnerable | Segura |
|---|---|---|
| SQL Injection | ❌ Vulnerable | ✅ Corregida |
| Stored XSS | ❌ Vulnerable | ✅ Corregida |
| IDOR en perfiles | ❌ Vulnerable | ✅ Corregida |
| IDOR en pedidos | ❌ Vulnerable | ✅ Corregida |
| Tokens Anti-CSRF | ❌ Ausentes | ✅ Implementados |
| Contraseñas | ❌ Texto plano | ✅ Hash |
| Consultas SQL | ❌ Concatenadas | ✅ Parametrizadas |
| CSP | ❌ Ausente | ✅ Implementada |
| X-Content-Type-Options | ❌ Ausente | ✅ Implementado |
| Anti-Clickjacking | ❌ Ausente | ✅ Implementado |
| Debug | ❌ Activado | ✅ Desactivado |
| Control de autorización | ❌ Insuficiente | ✅ Implementado |

---

# 22. Hallazgos principales

## Riesgo alto

1. SQL Injection.
2. Stored Cross-Site Scripting.
3. IDOR / Broken Access Control en perfiles.
4. IDOR / Broken Access Control en pedidos.

## Riesgo medio

1. Ausencia de protección Anti-CSRF.
2. Ausencia de Content Security Policy.
3. Falta de protección Anti-Clickjacking.

## Riesgo bajo / informativo

1. Divulgación de versiones de software.
2. Cabeceras HTTP adicionales ausentes.
3. Información de autenticación y sesión identificada.

---

# 23. Recomendaciones

- Utilizar consultas parametrizadas.
- Nunca almacenar contraseñas en texto plano.
- Aplicar autorización sobre cada recurso solicitado.
- Implementar tokens Anti-CSRF.
- Escapar contenido generado por usuarios.
- Utilizar CSP restrictiva.
- Configurar cabeceras HTTP de seguridad.
- Evitar divulgar versiones innecesarias.
- Deshabilitar debug en producción.
- Incorporar pruebas de seguridad al ciclo de desarrollo.
- Utilizar análisis automatizado como complemento de pruebas manuales.

---

# 24. Conclusiones

La práctica permitió comprobar que una aplicación funcional no necesariamente es segura. La versión vulnerable de ByteVault presentaba fallas relacionadas con validación de entradas, autenticación, autorización, almacenamiento de contraseñas y configuración HTTP.

WhatWeb, Nikto, Nmap y OWASP ZAP facilitaron la identificación de tecnologías, servicios y vulnerabilidades. Sin embargo, las pruebas manuales fueron fundamentales para confirmar SQL Injection, Stored XSS e IDOR.

Después de implementar controles de seguridad, las pruebas realizadas contra la segunda versión demostraron una reducción significativa de vulnerabilidades. Esto evidencia la importancia de integrar seguridad durante el desarrollo de aplicaciones.

---

# 25. Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| Kali Linux | Entorno de auditoría |
| WSL 2 | Ejecución de Kali Linux en Windows |
| Python | Ejecución de las aplicaciones |
| Flask | Framework web |
| SQLite | Base de datos |
| WhatWeb | Reconocimiento tecnológico |
| Nikto | Evaluación de configuración HTTP |
| Nmap | Identificación de puertos y servicios |
| OWASP ZAP | Análisis automatizado |
| GitHub Pages | Publicación del manual |

---

# 26. Referencias

- OWASP Foundation. *OWASP Web Security Testing Guide*.
- OWASP Foundation. *OWASP Top 10*.
- OWASP ZAP. *Zed Attack Proxy Documentation*.
- Kali Linux. *Kali Tools Documentation*.
- Nmap Project. *Nmap Reference Guide*.
- Flask Documentation. *Flask Web Development Framework*.

---

## Nota final

Este laboratorio fue diseñado únicamente con fines académicos para la asignatura **Seguridad y Auditoría de Sistemas**. Todas las vulnerabilidades fueron ejecutadas dentro de un entorno local controlado.
