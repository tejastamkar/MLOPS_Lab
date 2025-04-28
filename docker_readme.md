## Procedure Install Docker

### Download and install Docker Desktop from the official Docker website.
### Verify the installation:

```
$ docker --version
```


### Create a Simple Python Flask Application

### Create a new project folder and add a Python script app.py:

#### python code 
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello, Docker + Flask!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000)
```

## Create a requirements.txt file listing Flask:
```
Flask
```

## Write a Dockerfile for the Flask Application

### In the same folder, create a file named Dockerfile:
```
dockerfile
```

```
# Use official Python image
FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Copy code and requirements into container
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
COPY . .

# Command to run the app
CMD ["python", "app.py"]
```
## Build the Docker Image
Open a terminal in the project folder and build the Docker image:

```
docker build -t flask-docker-app .
```
## Run the Docker Container

Run the Flask application inside a container, mapping container port 5000 to localhost port 5000:
```
docker run -p 5000:5000 flask-docker-app
```

## Explore Basic Docker Commands

List all running containers:
```
docker ps
```
Stop a container:
```
docker stop <container_id>
```
Remove a container:
```
docker rm <container_id>
```
List all images:

```
docker images
```
