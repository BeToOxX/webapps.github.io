# Herramientas de auditoría

La práctica combina reconocimiento, análisis de servicios y pruebas de seguridad web.

## Kali Linux sobre WSL

Kali Linux proporciona un entorno orientado a seguridad. En esta práctica se ejecuta dentro de **WSL 2**, evitando instalar una máquina virtual completa.

## WhatWeb

**Objetivo:** identificar tecnologías visibles de una aplicación.

Permite detectar elementos como:

- servidor HTTP;
- lenguaje;
- framework;
- título;
- versiones expuestas.

```bash
whatweb http://IP:5000
```

## Nikto

**Objetivo:** buscar configuraciones inseguras y cabeceras ausentes.

```bash
nikto -h http://IP:5000
```

## Nmap

**Objetivo:** identificar puertos abiertos, servicios y versiones.

```bash
nmap -sV -p 5000 IP
```

## OWASP ZAP

**Objetivo:** analizar una aplicación web de forma automatizada y detectar posibles vulnerabilidades.

En el laboratorio se utiliza para:

- recorrer rutas con Spider;
- detectar SQL Injection;
- detectar XSS;
- identificar ausencia de CSRF;
- revisar cabeceras;
- clasificar alertas por riesgo.

## Herramientas vs. pruebas manuales

| Automatizada | Manual |
|---|---|
| Escanea muchos puntos rápidamente | Confirma el comportamiento real |
| Produce alertas | Permite comprender el impacto |
| Puede producir falsos positivos | Requiere conocimiento del flujo |
| Excelente para cobertura | Excelente para validación |

La práctica utiliza ambos enfoques.
