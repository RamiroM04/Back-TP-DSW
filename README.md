# Backend - Sistema de Gestión de Gimnasio

API REST desarrollada con **Node.js**, **Express** y **TypeScript**.

## Stack

| Tecnología | Uso |
| --- | --- |
| Node.js | Runtime |
| Express | Framework web |
| TypeScript | Lenguaje |
| ts-node-dev | Hot reload en desarrollo |

> **Base de datos**: por ahora los datos se almacenan en memoria (arrays). La integración con PostgreSQL o alguna BD se realizará en una etapa posterior; solo será necesario reemplazar la capa de repositorio.

---

## Estructura del proyecto

```markdown
src/
├── server.ts           # Entry point: levanta el servidor
├── app.ts              # Configura Express, middlewares y rutas
│
├── socio/
│   ├── socio.entity.ts       # Definición del tipo/clase de negocio
│   ├── socio.repository.ts   # Acceso a datos (hoy en memoria)
│   ├── socio.service.ts      # Lógica de negocio y validaciones
│   └── socio.router.ts       # Definición de rutas HTTP
│
├── actividad/
│   └── ...
└── instructor/
    └── ...
```

### Capas

La arquitectura sigue un modelo de capas. Cada feature (entidad de negocio) está organizada en su propia carpeta con las siguientes responsabilidades:

- **entity**: define la forma del objeto de negocio (interfaces/clases TypeScript)
- **repository**: único punto de acceso a los datos; al integrar una BD solo se modifica esta capa
- **service**: contiene la lógica de negocio, validaciones y reglas
- **router**: expone los endpoints HTTP y delega al service

---

## Instalación y ejecución

### Requisitos previos

- Node.js >= 18
- npm >= 9

### Pasos

```bash
# 1. Clonar el repositorio
git clone <url-del-repo>
cd backend

# 2. Instalar dependencias
npm install

# 3. Configurar variables de entorno
cp .env.example .env
# Editar .env si es necesario

# 4. Iniciar en modo desarrollo (hot reload)
npm run dev
```

El servidor estará disponible en `http://localhost:3000`.

### Scripts disponibles

| Script | Descripción |
| --- | --- |
| `npm run dev` | Inicia con hot reload para desarrollo |
| `npm run build` | Compila TypeScript a JavaScript en `/dist` |
| `npm start` | Ejecuta la versión compilada (producción) |

---

## Variables de entorno

Crear un archivo `.env` en la raíz:

```markdown
PORT=3000
```

---

## Endpoints disponibles

### Health check

```markdown
GET /health
```

Respuesta:

```json
{ "status": "ok" }
```

> Los endpoints de cada entidad se deberían documentar a medida que se implementen.
