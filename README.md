# TalentHub API

API REST de una **bolsa de empleo tech**: las empresas publican ofertas, los candidatos
suben su CV y se postulan, y un motor de matching calcula la compatibilidad entre perfil
y oferta. Construida con **FastAPI**, **SQLAlchemy 2.0** y **PostgreSQL**.

> 🚧 En construcción — progreso en [ROADMAP.md](ROADMAP.md).

## Funcionalidades (objetivo v1.0)

- Ofertas con slug, filtros (modalidad, seniority, salario), paginación y búsqueda full-text
- Empresas, categorías y skills (relación N—N con ofertas y candidatos)
- Subida de CV en PDF y logos
- Postulaciones con flujo de estados (`submitted → reviewing → interview → hired/rejected`)
- Autenticación JWT con roles `candidate`, `company` y `admin`
- Endpoints de IA desacoplados (matching CV↔oferta, extracción de skills, estimación
  salarial), servidos por implementaciones mock intercambiables
- Middlewares: CORS, request ID, tiempo de respuesta, rate limiting
- Migraciones con Alembic, tests con pytest, CI con GitHub Actions
- Desplegada en Render

## Stack previsto

FastAPI · Pydantic v2 · SQLAlchemy 2.0 · PostgreSQL · Alembic · PyJWT · httpx · pytest · Render

## Dependencias instaladas

Se añaden aquí a medida que se instalan en el proyecto.

| Paquete | Versión | Para qué | Fase |
|---|---|---|---|
| `fastapi[standard]` | 0.162.5 | Framework web. El extra `standard` incluye `uvicorn`, `fastapi-cli`, `httpx`, `jinja2`, `python-multipart` y `email-validator` | 0 |

Incluidas con `fastapi[standard]` (no hace falta instalarlas aparte): `uvicorn` 0.54.0
(servidor), `fastapi-cli` 0.0.33 (comando `fastapi dev`), `pydantic` 2.14.4 (validación),
`starlette` 1.7.0 (base de FastAPI), `httpx` 0.28.1 (cliente HTTP, también útil en tests),
`python-multipart` 0.0.32 (formularios y subida de archivos, Fase 8) y `email-validator` 2.4.0
(validar emails en Pydantic).

## Ejecutar en local

```bash
fastapi dev app/main.py
```

- API: http://127.0.0.1:8000/
- Swagger: http://127.0.0.1:8000/docs
- Parar el servidor: `Ctrl+C`

> Ejecutar desde la carpeta que contiene `app/` y con el entorno virtual activo.
> Si no, da `Path does not exist app/main.py` o `fastapi: command not found`.

Más comandos (entorno virtual, instalación…) en `COMANDOS.md`, en la raíz del repositorio.
