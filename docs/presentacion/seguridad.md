# Seguridad y objetivos de ataque

La seguridad de una aplicación web busca proteger la información, las operaciones y los usuarios frente a acciones no autorizadas.

## Triada CIA

### Confidencialidad

La información debe ser accesible únicamente por las personas autorizadas.

Ejemplos:

- datos personales;
- credenciales;
- pedidos;
- información financiera.

### Integridad

Los datos y operaciones no deben poder modificarse de forma no autorizada.

Ejemplos:

- cambiar precios;
- alterar pedidos;
- modificar permisos;
- manipular datos almacenados.

### Disponibilidad

El sistema debe continuar accesible cuando los usuarios legítimos lo necesiten.

## Objetivos frecuentes de un atacante

Un ataque contra una Web App puede buscar:

- **evadir autenticación** y acceder sin credenciales válidas;
- **elevar privilegios**;
- **leer información de otros usuarios**;
- **alterar registros**;
- **ejecutar código en el navegador de una víctima**;
- **extraer información de la base de datos**;
- **secuestrar sesiones**;
- **identificar versiones y componentes** para buscar debilidades conocidas;
- **interrumpir el servicio**.

## Superficie de ataque

La superficie de ataque es el conjunto de puntos que un usuario o sistema externo puede alcanzar.

En ByteVault incluye:

```text
/login
/catalog?q=
/reviews
/profile/<id>
/orders
/order/<id>
Cookies de sesión
Cabeceras HTTP
Puerto TCP 5000
```

## Defensa en profundidad

Una aplicación segura no depende de una sola protección.

Debe combinar:

- validación de entradas;
- consultas parametrizadas;
- autenticación robusta;
- autorización por recurso;
- hashing de contraseñas;
- protección CSRF;
- cabeceras HTTP;
- monitoreo y registro;
- configuración segura.
