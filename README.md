# VaultStore Web Security Lab

Documentación académica de la práctica de seguridad en aplicaciones web.

El sitio contiene:

- Preparación de Kali Linux en WSL.
- Instalación y ejecución del laboratorio.
- Reconocimiento con WhatWeb, Nikto y Nmap.
- Pruebas manuales de SQL Injection, Stored XSS e IDOR.
- Análisis con OWASP ZAP.
- Ejecución de la versión segura.
- Repetición de las pruebas para comprobar mitigaciones.
- Comparación de resultados.
- Glosario.

## Probar localmente

```bash
pip install -r requirements.txt
mkdocs serve
```

Abrir:

```text
http://127.0.0.1:8000
```

## Publicar en GitHub Pages

```bash
mkdocs gh-deploy --force
```
