# **Aplicación Web con Docker, PostgreSQL, Flask y NGINX**

Este proyecto es una aplicación web construida en Python con Flask, utilizando una base de datos PostgreSQL 
y configurada con NGINX como proxy. Toda la aplicación está contenida en una estructura de Docker 
con servicios separados para cada componente.

## **Estructura del Proyecto**

```plaintext
web-app/
|-- database/
|   |-- Dockerfile            # Dockerfile para la base de datos PostgreSQL
|   |-- init.sql              # sql para crear la tabla e insertar los datos en la base de datos
|   webapp/
|   |-- app/
|       |-- templates/
|           |-- index.html    # HTML para visualizar la aplicacion web
|       |-- __init__py        # Creacion y configurancion del Flask
|       |-- config.py         # Configuracion de la Base de Datos
|       |-- models.py         # Definicion del modelo de la Base de Datos
|       |-- routes.py         # Creacion de la ruta para la pagina web
|   |-- Dockerfile            # Dockerfile para la aplicación Flask en Python
|   |-- main.py               # Archivo principal donde se ejecuta la aplicacion web
|   |-- requirements.txt      # Dependencias para la aplicación                     
|-- proxy/
|   |-- Dockerfile            # Dockerfile para NGINX como proxy
|   |-- nginx.conf            # Configuracion del nginx
|-- .gitignore
|-- docker-compose.yml        # Configuración de Docker Compose para todos los servicios
|-- README.md                 # Documentación del proyecto
```

## **Dependencias**

- **Docker**: Para contenerizar cada servicio del proyecto.
- **Docker Compose**: Para gestionar y administrar los servicios.
- **Python**: Para crear y ejecutar la aplicación Flask.
- **PostgreSQL**: Como base de datos relacional.
- **NGINX**: Como proxy para manejar el tráfico HTTP.

## **Instalación**

**Clonar el repositorio**:

   **Nota:** Se debe tener instalado `git` para poder clonar el repositorio de GitHub y un entorno de desarrollo como Visual Studio Code con WSL o Ubuntu

   ```bash
   git clone https://github.com/NicolasMFDev/Web-App.git
   cd web-app
   ```

## Uso

### Construcción y Ejecución del Proyecto

1. **Construir y levantar los servicios con Docker Compose**:
   ```bash
   docker-compose up --build -d
   ```
   Este comando ejecutará los siguientes servicios:
   - **webapp**: Servicio de la aplicación Flask.
   - **database**: Servicio de la base de datos PostgreSQL.
   - **proxy**: Servicio de NGINX como proxy.

2. **Acceder a la aplicación**:
   - La aplicación estará disponible en `http://localhost` despues de ejecutar los contenedores.

### Comandos Útiles

- **Detener los contenedores**:
  ```bash
  docker-compose down
  ```

- **Reconstruir y reiniciar los contenedores**:
  ```bash
  docker-compose up --build -d
  ```

- **Revisar el funcionamiento de los contenedores mediante los logs**
  ```bash
  docker compose logs database  # Para la base de datos
  docker compose logs webapp    # Para la aplicacion web
  docker compose logs proxy     # Para el nginx
  ```

## Estructura del Código

- **database/**: Contiene la configuración de la base de datos y el Dockerfile para configurar el contenedor de `PostgreSQL`.
- **webapp/**: Contiene la lógica de la aplicación `Flask`, el archivo `requirements.txt` para instalar las dependencias específicas y el archivo `Dockerfile` para el contenedor de la aplicacion flask.
- **proxy/**: Contiene la configuración de NGINX, incluyendo un Dockerfile para personalizar su configuración.

## Autor

Creado por [Nicolas Martinez](https://github.com/NicolasMFDev)