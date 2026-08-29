# Análisis con OWASP ZAP

## 14. Análisis automatizado de VaultStore Vulnerable

Abrir **OWASP ZAP**.

En la pantalla principal seleccionar:

```text
Inicio Rápido
→ Escaneo Automatizado
```

### 14.1 URL objetivo

Durante la práctica:

```text
http://172.22.136.16:5000
```

Si la dirección de WSL es diferente, utilizar la IP obtenida con:

```bash
hostname -I
```

### 14.2 Configuración utilizada

```text
Política: Dev Standard
Spider tradicional: Activado
Modern Spider: Chrome
```

Iniciar el análisis y esperar a que ZAP finalice el recorrido y las pruebas.

### 14.3 Hallazgos principales

En la aplicación vulnerable se analizaron hallazgos como:

- Cross-Site Scripting.
- Inyección SQL.
- Ausencia de tokens Anti-CSRF.
- CSP no configurada.
- Falta de Anti-Clickjacking.
- Divulgación de información del servidor.
- Falta de `X-Content-Type-Options`.

### 14.4 SQL Injection detectada por ZAP

ZAP identificó puntos de entrada relacionados con:

```text
GET /catalog (q)
POST /login (username)
POST /login (password)
```

### 14.5 Interpretación

Los resultados de una herramienta automatizada deben revisarse manualmente. La existencia de una alerta no sustituye la validación técnica del hallazgo.
