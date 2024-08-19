Desarrolla una Guía de Aprendizaje para  el siguiente proyecto con  Django Mongo, React JS y todo Dockerizado  desarrolla  una introducción de los prerrequisitos  y creación de cada una de las carpetas asi como el levantamiento de cada entorno vent,  y proyectos django-admin startproject clientes   asi como el front npx create-react-app frontend todo esto para llevar acabo el proyecto completo además desarrolla descripciones explicativas claras definiciones y presenta paso a paso la configuraciones  de cada entorno permite al usuario que tenga una compresión y vaya de manera cronológica aprendiendo 
la estructura es 
mi_proyecto/
│
├── clientes/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│   └── clientes/
│       └── settings.py
│
├── proveedores/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│   └── proveedores/
│       └── settings.py
│
├── productos_servicios/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│   └── productos_servicios/
│       └── settings.py
│
├── facturacion/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│   └── facturacion/
│       └── settings.py
│
├── usuarios/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│   └── usuarios/
│       └── settings.py
│
├── frontend/
│   ├── Dockerfile
│   ├── src/
│   └── package.json
│
└── docker-compose.yml
los requements.txt que se usa es 
asgiref==3.8.1
Django==3.2
djongo==1.3.6
dnspython==2.6.1
pip==24.2
pymongo==4.8.0
pytz==2024.1
sqlparse==0.2.4
tzdata==2024.1

el posible compose.yml


version: '3.9'

services:
  mongo:
    image: mongo:latest
    container_name: mongo
    ports:
      - "27017:27017"
    volumes:
      - mongo_data:/data/db
      - ./mongo-init.js:/docker-entrypoint-initdb.d/mongo-init.js
    environment:
      - MONGO_INITDB_ROOT_USERNAME=admin
      - MONGO_INITDB_ROOT_PASSWORD=admin_password

  usuarios_backend:
    build: ./usuarios
    container_name: usuarios_backend
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - ./usuarios:/app
    ports:
      - "8000:8000"
    depends_on:
      - mongo
    environment:
      - MONGO_URI=mongodb://mongo:27017/usuarios_db

  clientes_backend:
    build: ./clientes
    container_name: clientes_backend
    command: python manage.py runserver 0.0.0.0:8001
    volumes:
      - ./clientes:/app
    ports:
      - "8001:8001"
    depends_on:
      - mongo
    environment:
      - MONGO_URI=mongodb://mongo:27017/clientes_db

  proveedores_backend:
    build: ./proveedores
    container_name: proveedores_backend
    command: python manage.py runserver 0.0.0.0:8002
    volumes:
      - ./proveedores:/app
    ports:
      - "8002:8002"
    depends_on:
      - mongo
    environment:
      - MONGO_URI=mongodb://mongo:27017/proveedores_db

  productos_servicios_backend:
    build: ./productos_servicios
    container_name: productos_servicios_backend
    command: python manage.py runserver 0.0.0.0:8003
    volumes:
      - ./productos_servicios:/app
    ports:
      - "8003:8003"
    depends_on:
      - mongo
    environment:
      - MONGO_URI=mongodb://mongo:27017/productos_servicios_db

  facturacion_backend:
    build: ./facturacion
    container_name: facturacion_backend
    command: python manage.py runserver 0.0.0.0:8004
    volumes:
      - ./facturacion:/app
    ports:
      - "8004:8004"
    depends_on:
      - clientes_backend
      - productos_servicios_backend
    environment:
      - MONGO_URI=mongodb://mongo:27017/facturacion_db

  frontend:
    build: ./frontend
    container_name: react_frontend
    ports:
      - "3000:3000"
    volumes:
      - ./frontend:/app
    depends_on:
      - usuarios_backend
      - clientes_backend
      - proveedores_backend
      - productos_servicios_backend
      - facturacion_backend

volumes:
  mongo_data:

