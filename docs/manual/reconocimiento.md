# 3. Reconocimiento

Mantén ByteVault vulnerable ejecutándose en `:5000` y abre otra terminal de Kali.

## WhatWeb

```bash
whatweb http://172.22.136.16:5000
```

Un resultado típico identifica:

```text
200 OK
HTML5
Werkzeug/3.1.3
Python/3.13.12
ByteVault Store
```

### Interpretación

La herramienta confirma que el servicio responde y muestra que el servidor expone información de sus tecnologías.

---

## Nikto

```bash
nikto -h http://172.22.136.16:5000
```

En la versión vulnerable pueden aparecer observaciones relacionadas con:

- `Content-Security-Policy`;
- `Referrer-Policy`;
- `X-Content-Type-Options`;
- `Permissions-Policy`;
- información de versión.

Si Nikto pregunta si deseas enviar información de actualización:

```text
(y/n)?
```

puedes responder:

```text
n
```

---

## Nmap

Escaneo general:

```bash
nmap 172.22.136.16
```

Detección sobre el puerto de ByteVault:

```bash
nmap -sV -p 5000 172.22.136.16
```

Resultado esperado:

```text
5000/tcp open http Werkzeug httpd 3.1.3 (Python 3.13.12)
```

### ¿Qué demuestra?

Nmap confirma:

- puerto abierto;
- protocolo HTTP;
- servidor identificado;
- versión visible.
