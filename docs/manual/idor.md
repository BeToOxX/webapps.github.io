# 6. IDOR / Broken Access Control

IDOR ocurre cuando la aplicación utiliza un identificador directo para acceder a un recurso sin comprobar correctamente si el usuario está autorizado.

## IDOR en perfiles

Autenticado como administrador:

```text
/profile/1
```

Modificar a:

```text
/profile/2
```

o:

```text
/profile/3
```

La versión vulnerable permite visualizar información de otras cuentas.

## IDOR en pedidos

El administrador puede ver sus pedidos desde:

```text
/orders
```

Pero también puede solicitar directamente:

```text
/order/3
/order/4
```

En la versión vulnerable se muestran pedidos pertenecientes a otras cuentas.

## Riesgo

<span class="risk-high">ALTO</span>

El problema puede exponer información sensible o permitir operaciones no autorizadas.

## Corrección en la versión segura

El recurso se consulta usando el usuario autenticado:

```sql
WHERE o.id = ?
AND o.user_id = ?
```

La solicitud debe cumplir simultáneamente:

```text
pedido solicitado
+
propietario autenticado
```

Si no coincide, el recurso no se devuelve.
