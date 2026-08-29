# Resultados de la práctica

La auditoría permitió observar diferencias claras entre una aplicación deliberadamente vulnerable y una versión con controles defensivos.

## Hallazgos principales

| Hallazgo | Nivel | OWASP 2025 |
|---|---|---|
| SQL Injection | <span class="risk-high">Alto</span> | A05 Inyección |
| Stored XSS | <span class="risk-high">Alto</span> | A05 Inyección |
| IDOR perfiles | <span class="risk-high">Alto</span> | A01 Control de Acceso |
| IDOR pedidos | <span class="risk-high">Alto</span> | A01 Control de Acceso |
| Anti-CSRF ausente | <span class="risk-medium">Medio</span> | Seguridad de solicitudes |
| CSP ausente | <span class="risk-medium">Medio</span> | A02 Configuración |
| Headers ausentes | <span class="risk-medium">Medio</span> | A02 Configuración |
| Versiones expuestas | <span class="risk-low">Bajo</span> | A02 Configuración |

## Herramientas y función

| Herramienta | Resultado principal |
|---|---|
| WhatWeb | Identificación tecnológica |
| Nikto | Configuración HTTP y headers |
| Nmap | Puerto y versión del servicio |
| OWASP ZAP | Detección automatizada de vulnerabilidades |
| Pruebas manuales | Confirmación del impacto |
