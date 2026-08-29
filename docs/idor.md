# IDOR

## ¿Qué significa IDOR?

**IDOR** significa **Insecure Direct Object Reference**.

Es una vulnerabilidad relacionada con controles de acceso insuficientes.

Ocurre cuando una aplicación utiliza identificadores para acceder a recursos, pero no verifica correctamente si el usuario tiene autorización para consultar dichos recursos.

---

## Ejemplo

Una aplicación puede utilizar una dirección como:

```text
/perfil/10
```

donde `10` representa el identificador de un usuario.

Si el usuario modifica manualmente la URL:

```text
/perfil/11
```

y puede consultar información perteneciente a otro usuario sin autorización, existe un problema de control de acceso.

---

## Riesgos

Una vulnerabilidad IDOR puede permitir:

- Consultar información de otros usuarios.
- Modificar recursos ajenos.
- Eliminar información.
- Acceder a archivos privados.
- Alterar operaciones que deberían estar restringidas.

---

## Prueba en VaultStore Vulnerable

VaultStore Vulnerable permite analizar una funcionalidad donde determinados recursos se identifican mediante valores numéricos.

El objetivo consiste en comprobar si cambiar el identificador permite acceder a información que no pertenece al usuario autenticado.

---

## Mitigación

La aplicación debe verificar la autorización en el servidor.

No es suficiente ocultar un botón o impedir una acción desde JavaScript.

Un control correcto debe comprobar:

1. Quién es el usuario.
2. Qué recurso solicita.
3. Si tiene autorización para acceder a ese recurso.

Ejemplo conceptual:

```python
if resource.user_id != current_user.id:
    abort(403)
```

---

## Buenas prácticas

- Comprobar autorización en cada solicitud.
- No confiar en identificadores proporcionados por el cliente.
- Implementar controles de acceso del lado del servidor.
- Aplicar el principio de mínimo privilegio.
- Registrar intentos de acceso no autorizado.
