# Manual técnico del laboratorio

El laboratorio está diseñado para ejecutarse en una computadora Windows utilizando Kali Linux dentro de WSL 2.

## Flujo completo

```text
Preparar Kali
   ↓
Levantar ByteVault vulnerable (:5000)
   ↓
WhatWeb → Nikto → Nmap
   ↓
SQL Injection → XSS → IDOR
   ↓
OWASP ZAP
   ↓
Levantar ByteVault segura (:5001)
   ↓
Repetir pruebas
   ↓
Comparar resultados
```

## Archivos

[:material-folder-zip: Descargar ByteVault Web Security Lab](../assets/downloads/bytevault_web_security_lab_v2.zip){ .md-button .md-button--primary }

## Puertos utilizados

| App | Puerto |
|---|---:|
| Vulnerable | 5000 |
| Segura | 5001 |

!!! warning
    No publiques la versión vulnerable en Internet. Déjala únicamente dentro del laboratorio local.
