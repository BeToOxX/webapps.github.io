# Introducción

## Seguridad en aplicaciones web

Las aplicaciones web forman parte fundamental de los sistemas de información modernos. Actualmente son utilizadas para realizar operaciones comerciales, administrativas, bancarias, educativas y empresariales.

Debido a que estas aplicaciones pueden procesar información sensible y estar disponibles a través de Internet, representan un objetivo importante para diferentes tipos de ataques.

La seguridad web busca proteger tanto la aplicación como los datos que procesa, aplicando controles que reduzcan la posibilidad de accesos no autorizados, manipulación de información o interrupciones del servicio.

---

## Principios fundamentales de seguridad

Uno de los modelos más conocidos dentro de la seguridad de la información es la tríada CIA.

### Confidencialidad

Garantiza que la información únicamente pueda ser consultada por usuarios autorizados.

### Integridad

Busca evitar que la información sea modificada de manera no autorizada.

### Disponibilidad

Garantiza que los sistemas y la información puedan ser utilizados cuando sean necesarios.

---

## Seguridad durante el desarrollo

La seguridad no debería implementarse únicamente después de desarrollar una aplicación.

Debe considerarse durante todo el ciclo de vida del software, incluyendo:

1. Análisis.
2. Diseño.
3. Desarrollo.
4. Pruebas.
5. Implementación.
6. Mantenimiento.

Entre las principales prácticas se encuentran:

- Validación de entradas.
- Autenticación segura.
- Autorización.
- Gestión adecuada de sesiones.
- Protección de datos sensibles.
- Consultas parametrizadas.
- Codificación segura de contenido.
- Gestión de errores.
- Registro de eventos.
- Actualización de dependencias.

---

## Aplicación utilizada

Para el laboratorio se utiliza **VaultStore**, una aplicación web creada con fines académicos.

El objetivo es demostrar de manera controlada el funcionamiento de distintas vulnerabilidades para posteriormente analizar los controles necesarios para prevenirlas.

Las principales vulnerabilidades estudiadas son:

- SQL Injection.
- Stored XSS.
- IDOR.
- Configuraciones de seguridad detectables mediante OWASP ZAP.
