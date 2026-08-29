# Presentación: Seguridad en Web Applications

Esta sección funciona como la parte teórica de la exposición. Puede recorrerse directamente desde el menú lateral antes de iniciar la demostración práctica.

## Contenido de la presentación

<div class="grid cards" markdown>

-   :material-web:{ .lg .middle } **¿Qué es una Web App?**

    Componentes, arquitectura cliente-servidor y flujo de una petición.

-   :material-target:{ .lg .middle } **Objetivos de un ataque**

    Qué intenta comprometer un atacante y qué activos necesita proteger una aplicación.

-   :material-shield-alert:{ .lg .middle } **OWASP Top 10:2025**

    Principales categorías actuales de riesgo en aplicaciones web.

-   :material-tools:{ .lg .middle } **Herramientas**

    WhatWeb, Nikto, Nmap y OWASP ZAP.

</div>

## Presentación original

También se incluye el archivo PowerPoint que acompaña esta documentación:

[:material-file-powerpoint: Descargar presentación Web Applications](../assets/downloads/presentacion_webapps_seguridad.pptx){ .md-button .md-button--primary }

## Relación con el laboratorio

La teoría se conecta directamente con ByteVault:

| Concepto | Ejemplo en ByteVault |
|---|---|
| Inyección | SQL Injection en login y catálogo |
| XSS | Reseñas almacenadas sin escape |
| Control de acceso | IDOR en perfiles y pedidos |
| Configuración incorrecta | Cabeceras HTTP ausentes |
| Autenticación | Bypass del login en la versión vulnerable |
| Mitigación | Consultas parametrizadas, CSRF, headers y autorización |
