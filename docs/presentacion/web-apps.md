# ¿Qué es una aplicación web?

Una **aplicación web** es software que se ejecuta principalmente en un servidor y que el usuario utiliza mediante un navegador. A diferencia de una página web puramente informativa, una Web App suele manejar lógica de negocio, autenticación, formularios, bases de datos, sesiones y operaciones dinámicas.

## Componentes principales

```text
Usuario / Navegador
        │
        │ HTTP / HTTPS
        ▼
Servidor Web / Aplicación
        │
        ├── Lógica de negocio
        ├── Autenticación y sesión
        ├── API / Endpoints
        │
        ▼
     Base de datos
```

### Cliente

El navegador interpreta HTML, CSS y JavaScript y envía solicitudes al servidor.

### Servidor

Procesa la lógica de la aplicación, valida las solicitudes y determina qué información puede consultar o modificar cada usuario.

### Base de datos

Almacena información como usuarios, contraseñas, pedidos, productos, comentarios y configuraciones.

## Flujo básico de una petición

1. El usuario abre una URL.
2. El navegador envía una petición HTTP.
3. El servidor identifica la ruta solicitada.
4. La aplicación procesa parámetros y datos.
5. Si es necesario, consulta la base de datos.
6. El servidor devuelve una respuesta.
7. El navegador muestra el resultado.

## ¿Dónde aparecen los riesgos?

Los problemas de seguridad pueden surgir en cualquier punto:

- entradas de formularios;
- parámetros de URL;
- cookies y sesiones;
- consultas a la base de datos;
- autorización de recursos;
- respuestas HTML;
- cabeceras HTTP;
- dependencias y componentes externos.

!!! info "Idea clave"
    Un navegador no sabe si un dato proviene de un usuario legítimo o de un atacante. La aplicación debe validar, autorizar y procesar correctamente cada entrada.
