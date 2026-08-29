# Herramientas de Auditoría

Durante una evaluación de seguridad pueden utilizarse diferentes herramientas para identificar vulnerabilidades y analizar el comportamiento de una aplicación.

En este laboratorio se utilizan principalmente herramientas disponibles en Kali Linux.

---

## Kali Linux

Kali Linux es una distribución basada en Linux orientada a pruebas de penetración, análisis forense y auditoría de seguridad.

Incluye múltiples herramientas especializadas para evaluar:

- Aplicaciones web.
- Redes.
- Sistemas operativos.
- Servicios.
- Protocolos.
- Credenciales.
- Configuraciones.

---

## Navegador web

El navegador es una de las herramientas básicas para analizar una aplicación web.

Permite observar:

- Formularios.
- Parámetros.
- URLs.
- Cookies.
- Sesiones.
- Solicitudes HTTP.
- Respuestas del servidor.

Las herramientas de desarrollo del navegador también permiten inspeccionar código HTML, JavaScript y tráfico de red.

---

## cURL

`curl` permite realizar solicitudes HTTP directamente desde una terminal.

Ejemplo:

```bash
curl http://127.0.0.1:5000
```

También puede utilizarse para observar encabezados:

```bash
curl -I http://127.0.0.1:5000
```

---

## OWASP ZAP

**OWASP ZAP**, también conocido como **Zed Attack Proxy**, es una herramienta utilizada para analizar la seguridad de aplicaciones web.

Permite:

- Interceptar tráfico HTTP y HTTPS.
- Analizar encabezados.
- Detectar configuraciones inseguras.
- Ejecutar escaneos automatizados.
- Revisar solicitudes y respuestas.
- Identificar posibles vulnerabilidades.

---

## Herramientas adicionales

En auditorías web también pueden utilizarse herramientas como:

- Nmap.
- Burp Suite.
- Nikto.
- Gobuster.
- ffuf.
- sqlmap.

La utilización de una herramienta depende del objetivo y alcance de la evaluación.
