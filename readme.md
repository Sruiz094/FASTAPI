# Proyecto de elaboración de una API utilizado FastAPI 

Este es un proyecto educativo en el cual se creo una API REST simple creada con Python versión 3.10.12, FastAPI, docker y base de datos Postgresql.La API esta diseñada para realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar). 

## Requisitos previos

- Docker y Docker Compose instalados en tu máquina. Preferiblemente con [docker desktop](https://www.docker.com/products/docker-desktop/)
- [pyenv](https://github.com/pyenv/pyenv#installation)


## Instalación

* Clona este repositorio en tu maquina local: 
git clone https://github.com/Sruiz094/FastAPI.git

## Configuraciones iniciales

* Crea un archivo .env en la raíz del proyecto con las siguientes variables:

```text
ENVIRONMENT=
DEBUG=
STATUS_ENV=

MONGO_HOST=
MONGO_PORT=27017
MONGO_USER=
MONGO_PASS=
MONGO_DB=
MONGO_COLLECTION=
MONGO_TEST_DB=

MONGO_URL=
MONGO_URL_test=
```

## Configuración del proyecto con Docker
Este proyecto fue elaborado con docker, por ende, se suguiere configurar el proyecto utilizado docker, 
sin embargo, tambien se puede realizar la instalación con pyenv y poetry
```bash
docker compose --profile web  build
docker compose --profile web  up
```

## Ejecute la aplicación con: 

```bash
uvicorn sql_app.main:app --reload 
```

