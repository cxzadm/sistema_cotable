# Nombre del Proyecto

Descripción breve del proyecto. Este proyecto es una aplicación web completa utilizando Docker, con varios servicios backend, un frontend en React, y una base de datos MongoDB.

## Tabla de Contenidos

- [Descripción](#descripción)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Puertos Utilizados](#puertos-utilizados)
- [Instalación](#instalación)
- [Uso](#uso)
- [Contribución](#contribución)
- [Licencia](#licencia)

## Descripción

El proyecto se compone de múltiples servicios backend (clientes, proveedores, productos/servicios y facturación) y un frontend desarrollado en React. Todos los servicios están gestionados a través de Docker, lo que facilita la configuración y despliegue del proyecto.

## Estructura del Proyecto

El proyecto sigue la siguiente estructura de carpetas:

cx_project/
├── backend/
│ ├── clientes_backend/
│ │ ├── Dockerfile
│ │ ├── requirements.txt
│ │ ├── manage.py
│ │ └── (código fuente Django)
│ ├── proveedores_backend/
│ │ ├── Dockerfile
│ │ ├── requirements.txt
│ │ ├── manage.py
│ │ └── (código fuente Django)
│ ├── productos_servicios_backend/
│ │ ├── Dockerfile
│ │ ├── requirements.txt
│ │ ├── manage.py
│ │ └── (código fuente Django)
│ └── facturacion_backend/
│ ├── Dockerfile
│ ├── requirements.txt
│ ├── manage.py
│ └── (código fuente Django)
├── frontend/
│ ├── Dockerfile
│ └── (código fuente React)
├── docker-compose.yml
└── README.md


## Puertos Utilizados

A continuación se detallan los puertos expuestos por los diferentes servicios:

- **Clientes Backend:** `0.0.0.0:8001` -> `8001/tcp`
- **Proveedores Backend:** `0.0.0.0:8002` -> `8002/tcp`
- **Productos/Servicios Backend:** `0.0.0.0:8003` -> `8003/tcp`
- **Facturación Backend:** `0.0.0.0:8004` -> `8004/tcp`
- **Frontend React:** `0.0.0.0:3000` -> `3000/tcp`
- **MongoDB:** `0.0.0.0:27017` -> `27017/tcp`

## Instalación

Para instalar y ejecutar el proyecto localmente, sigue estos pasos:

1. **Clona el repositorio:**

   ```bash
   git clone https://github.com/usuario/nombre-del-repositorio.git

2 Navega a la carpeta del proyecto:

cd nombre-del-repositorio

3 Construye y ejecuta los contenedores Docker:

docker-compose up --build

4 Configura las variables de entorno (si es necesario):

Asegúrate de crear un archivo .env en la raíz del proyecto con las configuraciones necesarias para los diferentes servicios.

Uso
Una vez que los contenedores estén corriendo, puedes acceder a los diferentes servicios a través de los siguientes URLs:

Clientes Backend: http://localhost:8001
Proveedores Backend: http://localhost:8002
Productos/Servicios Backend: http://localhost:8003
Facturación Backend: http://localhost:8004
Frontend React: http://localhost:3000
Contribución
Si deseas contribuir al proyecto, sigue estos pasos:

Haz un fork del repositorio.
Crea una nueva rama (git checkout -b feature/nueva-caracteristica).
Haz tus cambios y realiza un commit (git commit -am 'Añade nueva característica').
Empuja la rama (git push origin feature/nueva-caracteristica).
Crea un pull request.

## Licencia
Este proyecto está bajo la licencia [Nombre de la Licencia]. Consulta el archivo LICENSE para más detalles.

Puedes copiar y pegar este contenido directamente en un archivo `README.md` para documentar tu proyecto. ¡Espero que te sea útil!


python3 -m venv venv  

django-admin startproject clientes . 

python -m django startproject clientes .


estado del mogo
docker exec -it mongo mongo




elimiar chache docker

docker system prune --all --volumes


reecostruye docker 

docker-compose up --build






1.........

mkdir -p cx_project/clientes/clientes
mkdir -p cx_project/proveedores/proveedores
mkdir -p cx_project/productos_servicios/productos_servicios
mkdir -p cx_project/facturacion/facturacion
mkdir -p cx_project/usuarios/usuarios
mkdir -p cx_project/frontend/src


2......................

pip install django

django-admin startproject clientes   ## python -m django startproject clientes .

pip install djongo


mkdir servicio
cd servicio
python -m venv venv
.\venv\Scripts\activate
pip install django
django-admin startproject servicio .
deactivate
cd ..


requerimientos
pip freeze > requirements.txt

instalar  archivo de 

pip install -r requirements.txt


frontend ..............

npx create-react-app frontend


reiniciar contendedores ..........

docker restart usuarios_backend
docker-compose down
docker-compose up -d
