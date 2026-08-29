# Conclusiones

La seguridad en aplicaciones web es un componente fundamental durante el desarrollo de sistemas modernos, especialmente cuando una aplicación procesa información sensible o se encuentra disponible a través de una red.

Durante el laboratorio de VaultStore fue posible analizar diferentes vulnerabilidades comunes y comprender el impacto que pueden generar cuando una aplicación no implementa correctamente mecanismos de protección.

SQL Injection permitió observar la importancia de utilizar consultas parametrizadas y evitar la construcción dinámica de sentencias SQL utilizando directamente información proporcionada por los usuarios.

Stored XSS permitió analizar los riesgos asociados con representar contenido no confiable dentro de una página web sin aplicar controles adecuados de codificación, escape o sanitización.

El análisis de IDOR demostró que la autenticación por sí sola no garantiza la seguridad de los recursos. Una aplicación también debe comprobar que cada usuario tenga autorización para realizar la operación solicitada.

OWASP ZAP permitió complementar las pruebas manuales mediante el análisis de solicitudes, respuestas HTTP y configuraciones relacionadas con la seguridad de la aplicación.

Finalmente, la comparación entre VaultStore Vulnerable y VaultStore Secure permitió demostrar que la incorporación de buenas prácticas durante el desarrollo puede reducir considerablemente la superficie de ataque de una aplicación.

La seguridad debe considerarse durante todo el ciclo de vida del software y no únicamente después de que el sistema se encuentre terminado.
