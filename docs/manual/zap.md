# 7. Análisis con OWASP ZAP

OWASP ZAP se ejecuta en Windows mientras ByteVault continúa funcionando dentro de Kali/WSL.

## Escaneo de la vulnerable

Abrir:

```text
Inicio Rápido
→ Escaneo Automatizado
```

URL:

```text
http://172.22.136.16:5000
```

Configuración utilizada:

```text
Política de Escaneo: Dev Standard
Spider tradicional: activado
Modern Spider: Chrome
```

Presionar:

```text
Atacar
```

## Alertas observadas en la vulnerable

ZAP puede identificar:

- Cross-Site Scripting;
- Inyección SQL;
- ausencia de tokens Anti-CSRF;
- CSP no configurada;
- falta de protección Anti-Clickjacking;
- divulgación de versión;
- falta de `X-Content-Type-Options`.

### SQL Injection detectada

Dentro de la práctica se identificaron puntos como:

```text
GET /catalog (q)
POST /login (username)
POST /login (password)
```

## Importante sobre la confianza

Una alerta automatizada no debe interpretarse siempre como confirmación absoluta.

Por ejemplo, ZAP puede marcar SQL Injection con confianza baja si un carácter genera un error HTTP 500. Por eso las pruebas manuales complementan al análisis automatizado.

## Separar sesiones

Para no mezclar alertas:

```text
Sesión 1 → ByteVault vulnerable :5000
Sesión 2 → ByteVault segura     :5001
```

Así la comparación es más clara.
