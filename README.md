# Web Applications Security — MkDocs Material

Sitio de documentación para la práctica de **Seguridad y Auditoría de Sistemas**.

Incluye:

- presentación teórica;
- OWASP Top 10:2025;
- manual completo de ByteVault;
- herramientas de auditoría;
- SQL Injection;
- Stored XSS;
- IDOR;
- OWASP ZAP;
- aplicación segura;
- comparación y conclusiones;
- presentación PPTX y laboratorio ZIP descargables.

## Estructura

```text
.
├── mkdocs.yml
├── requirements.txt
├── .github/
│   └── workflows/
│       └── ci.yml
└── docs/
    ├── index.md
    ├── presentacion/
    ├── manual/
    ├── resultados/
    └── assets/
```

## Subir al repositorio

Sube **el contenido de esta carpeta a la raíz del repositorio**, no la carpeta completa.

Debe verse así en GitHub:

```text
mkdocs.yml
requirements.txt
docs/
.github/
README.md
```

## GitHub Pages

El workflow genera automáticamente una rama llamada:

```text
gh-pages
```

Después del primer despliegue:

1. Ve a **Settings → Pages**.
2. En **Build and deployment**, selecciona **Deploy from a branch**.
3. Selecciona:
   - Branch: `gh-pages`
   - Folder: `/ (root)`
4. Guarda.

La página actual del repositorio sería aproximadamente:

`https://betooxx.github.io/webapps.github.io/`

Si cambias el nombre del repositorio a `web-apps`, cambia en `mkdocs.yml`:

```yaml
site_url: https://betooxx.github.io/web-apps/
```

## Vista previa local

```bash
pip install -r requirements.txt
mkdocs serve
```

Luego abre:

`http://127.0.0.1:8000`
