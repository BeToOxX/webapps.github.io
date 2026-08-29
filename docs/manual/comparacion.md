# 9. Comparación final

## Vulnerable vs. segura

| Control / vulnerabilidad | `:5000` Vulnerable | `:5001` Segura |
|---|---|---|
| SQL Injection | <span class="vulnerable">Vulnerable</span> | <span class="secure">Corregida</span> |
| Stored XSS | <span class="vulnerable">Vulnerable</span> | <span class="secure">Corregida</span> |
| IDOR perfiles | <span class="vulnerable">Vulnerable</span> | <span class="secure">Corregida</span> |
| IDOR pedidos | <span class="vulnerable">Vulnerable</span> | <span class="secure">Corregida</span> |
| Anti-CSRF | Ausente | Implementado |
| Contraseñas | Texto plano | Hash |
| SQL | Concatenación | Parámetros |
| CSP | Ausente | Implementada |
| Anti-Clickjacking | Ausente | Implementado |
| X-Content-Type-Options | Ausente | Implementado |
| Debug | Activado | Desactivado |

## Escaneo ZAP

En la versión segura dejan de aparecer los hallazgos críticos que se observaron en la vulnerable, especialmente:

- SQL Injection;
- XSS explotable;
- ausencia de Anti-CSRF;
- falta de `X-Content-Type-Options`;
- ausencia de protección Anti-Clickjacking.

Pueden continuar apareciendo recomendaciones de endurecimiento, por ejemplo relacionadas con CSP o la información de versión del servidor.

!!! success "Resultado"
    La finalidad no es obtener cero alertas, sino demostrar que los controles implementados eliminan las vulnerabilidades principales y reducen la superficie de ataque.
