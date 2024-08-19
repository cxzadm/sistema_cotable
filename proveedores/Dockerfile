# Dockerfile para aplicaciones Django
FROM python:3.10-slim

# Establece el directorio de trabajo en el contenedor
WORKDIR /app

# Copia el archivo de requisitos y el código fuente
COPY requirements.txt /app/
COPY . /app/

# Instala las dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Expone el puerto en el que la aplicación se ejecutará
EXPOSE 8002

# Ejecuta el servidor de desarrollo de Django
CMD ["python", "manage.py", "runserver", "0.0.0.0:8002"]
