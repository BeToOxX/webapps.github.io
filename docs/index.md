<div class="hero" markdown>

# Web Applications Security

**Presentación + laboratorio práctico** de seguridad y auditoría de aplicaciones web.

El sitio reúne en un mismo lugar la teoría necesaria para explicar qué es una aplicación web, los objetivos de un ataque, OWASP Top 10 y las herramientas de auditoría; además contiene el manual completo del laboratorio **ByteVault**, comparando una aplicación vulnerable contra una versión corregida.

<div class="hero-badges">
<span class="hero-badge">Kali Linux + WSL</span>
<span class="hero-badge">WhatWeb</span>
<span class="hero-badge">Nikto</span>
<span class="hero-badge">Nmap</span>
<span class="hero-badge">OWASP ZAP</span>
<span class="hero-badge">SQL Injection</span>
<span class="hero-badge">XSS</span>
<span class="hero-badge">IDOR</span>
</div>

</div>

!!! warning "Entorno académico y controlado"
    Las pruebas descritas en este sitio deben realizarse únicamente contra sistemas propios o para los cuales exista autorización expresa. En este laboratorio los ataques se ejecutan exclusivamente contra **ByteVault**, una aplicación creada deliberadamente para la práctica.

<div class="grid cards" markdown>

-   :material-presentation-play:{ .lg .middle } **Presentación**

    ---

    Conceptos de Web Apps, arquitectura, seguridad, objetivos de ataque y OWASP Top 10:2025.

    [:octicons-arrow-right-24: Ir a la presentación](presentacion/index.md)

-   :material-shield-bug:{ .lg .middle } **Manual técnico**

    ---

    Instalación, ejecución, reconocimiento y explotación controlada de ByteVault.

    [:octicons-arrow-right-24: Abrir el manual](manual/index.md)

-   :material-shield-check:{ .lg .middle } **Comparación**

    ---

    Diferencias entre la aplicación vulnerable y la aplicación segura.

    [:octicons-arrow-right-24: Ver resultados](resultados/index.md)

-   :material-download:{ .lg .middle } **Archivos del laboratorio**

    ---

    Descarga la aplicación y la presentación original.

    [:material-file-powerpoint: Presentación PPTX](assets/downloads/presentacion_webapps_seguridad.pptx){ .md-button }
    [:material-folder-zip: ByteVault ZIP](assets/downloads/bytevault_web_security_lab_v2.zip){ .md-button }

</div>

## Recorrido recomendado

<div class="flow">

**1. Presentación → 2. Preparar Kali → 3. Levantar ByteVault vulnerable → 4. Reconocimiento → 5. SQLi/XSS/IDOR → 6. OWASP ZAP → 7. ByteVault segura → 8. Comparación y conclusiones**

</div>

## ¿Qué se busca demostrar?

Una aplicación puede funcionar correctamente desde el punto de vista del usuario y, al mismo tiempo, contener vulnerabilidades graves. La práctica demuestra cómo los errores de desarrollo y configuración pueden permitir:

- evadir autenticación;
- ejecutar código en el navegador;
- consultar información de otros usuarios;
- exponer información del servidor;
- reducir los controles de seguridad disponibles en el navegador.

Después se aplican controles defensivos y se repiten las pruebas para comprobar la diferencia.
