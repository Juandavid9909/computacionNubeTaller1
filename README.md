# Taller 1 - Despliegue de Servicios de Red

**Autor:** Juan David Varela  
**Curso:** Computación Distribuida y Frameworks para Desarrollo de Aplicaciones Inteligentes - Universidad del Valle

Este repositorio contiene los scripts utilizados en el taller para consultar datos históricos de acciones desde Yahoo Finance (`yfinance`) y exponerlos como un servicio web mediante Flask dentro de un contenedor de Docker.

## Archivos

- `read_value_yf.py`: script que descarga los datos de una acción (por defecto `GOOGL` desde `2020-01-01` hasta la fecha actual).
- `app.py`: aplicación en Flask que expone el resultado en formato HTML en el puerto `5000`.
- `requirements.txt`: librerías necesarias (`yfinance` y `flask`).
- `Dockerfile`: configuración para construir la imagen del contenedor con Python 3.11.

## Uso con Docker

Construir la imagen localmente:

```bash
docker image build -t stock-market:2.0 .
```

Ejecutar el contenedor en local:

```bash
docker container run --rm --name stock-market -p 5000:5000 stock-market:2.0
```

Luego abrir `http://localhost:5000` en el navegador.

## Imagen en Docker Hub

La imagen publicada se encuentra en `varelajuan860/stock-market:2.0`. Para descargarla y correrla directamente (por ejemplo en una instancia EC2 en el puerto 80):

```bash
docker container run -d --rm --name stock-market -p 80:5000 varelajuan860/stock-market:2.0
```

