# Creando una API utilizado FastAPI 

Este es un proyecto educativo en el cual se creo una API REST simple creada con Python versión 3.10.12, FastAPI, docker y base de datos Postgresql.La API esta diseñada para realizar operaciones (Crear, Leer y Actualizar). 

## Requisitos previos

- Docker y Docker Compose instalados en tu máquina. Preferiblemente con [docker desktop](https://www.docker.com/products/docker-desktop/)
  
- [pyenv](https://github.com/pyenv/pyenv#installation)


## Instalación

* Clona este repositorio en tu maquina local:
  
* git clone https://github.com/Sruiz094/FastAPI.git

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
uvicorn sql_app.main:app --port 8001 --reload 
```

## API Endpoints

Obtener una lista de los usuarios de la base de datos 

```
GET /users
```
Respuesta 

```
[
  {
    "email": "jhonruiz094@gmail.com",
    "id": 1,
    "is_active": true,
    "items": [
      {
        "title": "Moto",
        "description": "KTM DUKE 200 NG",
        "id": 1,
        "owner_id": 1
      }
    ]
  },
  {
    "email": "sebastianruizm@utp.edu.co",
    "id": 2,
    "is_active": true,
    "items": []
  },
  {
    "email": "string",
    "id": 3,
    "is_active": true,
    "items": []
  },
  {
    "email": "correo@gmail.com",
    "id": 4,
    "is_active": true,
    "items": []
  }
]
```

# Creación de usuarios
```
Post/users/
```
Agrega un nuevo usuario al sistema. El cuerpo de la solicitud debe incluir un objeto JSON con las siguientes propiedades:

* "email"(cadena, obligatoria): la dirección de correo electrónico del usuario
  
* "password"(cadena, obligatoria): la contraseña del usuario

Parametros 

```{
  "email": "correo@gmail.com",
  "password": "xzy22*#"
}

```
Respuesta 

```
curl -X 'POST' \
  'http://127.0.0.1:8001/users/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "email": "correo@gmail.com",
  "password": "xyz22*#"
}'
```

# Consulta de ususario por id 

```
GET /users/{user_id}
```
Retorna los atributos del usuario consultado user_id: 4
Respuesta 

```
{
  "email": "correo@gmail.com",
  "id": 4,
  "is_active": true,
  "items": []
}
```

# Crear items para un usuario especifico 

```
Post/users/{user_id}/items/
```
Crea un items para un usuario especifico {user_id}/items/
El cuerpo de la solicitud debe incluir un objeto JSON con las siguientes propiedades:

* "title"(cadena): título de nuevo items o artículo a crear
  
* "description"(cadena): descripción del items creado

Respuesta 
```
curl -X 'POST' \
  'http://127.0.0.1:8001/users/1/items/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "Carro",
  "description": "Mazda 3"
}'

```


# Consultar los items creados 

```
GET/items/
```
Retorna los items creados en la base de datos 

Respuesta 
```
[
  {
    "title": "Moto",
    "description": "KTM DUKE 200 NG",
    "id": 1,
    "owner_id": 1
  },
  {
    "title": "Carro",
    "description": "Mazda 3",
    "id": 2,
    "owner_id": 1
  }
]
```



