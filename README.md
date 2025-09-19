# SimpleCRM Infra

**SimpleCRM Infra** es el proyecto de la **ingfraestructura del desarrollo** del ecosistema **SimpleCRM**, encargado de proveer los servicios de bases de datos y soporte para los distintos microservicios.
Construido con **Docker Compose**, este repositorio permite levantar fácilmente los contenedores necesarios para trabajar en entornos locales.

---

## 🚀 Funcionalidades principales

- Orquestación de contenedores con **Docker Compose**.
- Bases de datos independientes para cada servicio.
    - `auth_db` -> utilizada por simplecrm-auth-service.
    - `crm_db` -> utilizada por simplecrm-crm_service.
- Configuración de usuarios, contraseñas y puertos desde archivos `.env`.
- Entornos desechables: al no usar volúmenes persistentes, los datos se reinician en cada ciclo de ejecución.

---

## 📂 Estructura del proyecto

``` text
simplecrm-infra/
├─ .env.dev              # Variables de entorno para el desarrollo
├─ .gitignore
├─ docker-compose.yml    # Definición de servicios
└─ README.md             # Documentación del proyecto
```

---

## ⚙️ Requisitos previos

- Docker
- Docker Compose
- Gestor de base de datos externo para visualizar/administrar las DBs

---

## ▶️ Ejecución en desarrollo

### 1. Clona este repositorio

```bash
git clone git@github.com:JonathanNavarroV/simplecrm-infra.git
cd simplecrm-infra
```

### 2. Configura el archivo `.env.dev`:

Ejemplo básico:
```ini
# PostgreSQL Auth
POSTGRES_USER_AUTH=postgres
POSTGRES_PASSWORD_AUTH=postgres
AUTH_DB=auth_db

# PostgreSQL CRM
POSTGRES_USER_CRM=postgres
POSTGRES_PASSWORD_CRM=postgres
CRM_DB=crm_db
```

### 3. Levanta los contenedores:

```bash
docker compose --env-file .env.dev up -d
```
Esto levantará:
- `postgres-auth` en `localhost:5001`
- `postgres-crm` en `localhost:5002`

### 4. Detener los contenedores:

```bash
docker compose stop
```

Para volver a iniciarlos:
```
docker compose start
```

Para eliminarlos completamente:
``` bash
docker compose down
```

---

## 🔗 Repositorios relacionados

- [simplecrm-frontend](https://github.com/JonathanNavarroV/simplecrm-frontend)
- [simplecrm-gateway](https://github.com/JonathanNavarroV/simplecrm-gateway)
- [simplecrm-auth-service](https://github.com/JonathanNavarroV/simplecrm-auth-service)
- [simplecrm-crm-service](https://github.com/JonathanNavarroV/simplecrm-crm-service)

---

## ✨ Autor

[Jonathan Navarro](https://github.com/JonathanNavarroV)