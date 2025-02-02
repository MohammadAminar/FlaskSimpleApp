# FlaskSimpleApp

This is a simple Flask application that runs inside a Docker container and uses Nginx as a reverse proxy. The project demonstrates how to containerize a Flask app and use Nginx to handle incoming requests.

## Project Structure
```
flaskproject/
├── app/                  # Flask application folder
│   ├── app.py            # Main Flask application file
│   └── Dockerfile        # Dockerfile for the Flask app
├── docker-compose.yml    # Docker Compose file to manage services
├── nginx/                # Nginx configuration folder
│   ├── default.conf      # Nginx configuration file
│   └── Dockerfile        # Dockerfile for the Nginx service
└── requirements.txt      # Python dependencies for the Flask app
```

## How It Works
- **Flask Application**: The Flask app runs on port 5000 inside a Docker container.

- **Nginx**: Nginx acts as a reverse proxy, listening on port 80 and forwarding requests to the Flask app.

- **Docker Compose**: Manages the multi-container setup, making it easy to build and run the services.


## Prerequisites
- Docker installed on your machine.

- Docker Compose installed on your machine.

## Getting Started
1. **Clone the repository**:
```
git clone https://github.com/MohammadAminar/flask-docker-nginx-example.git
cd flask-docker-nginx-example
```

2. **Build and run the containers**:
```
docker-compose up --build
```

3. **Access the application**:
- Open your browser and go to `http://localhost`.
- You should see the message: `Hello, World by Docker!`

### Services
Flask App (`web` service)
- **Port**: 5000

- **Dockerfile**: Located in `app/Dockerfile`.

- **Description**: A simple Flask application that returns a greeting message.

### Nginx (`nginx` service)
- **Port**: 80

- **Dockerfile**: Located in `nginx/Dockerfile`.

- **Description**: Nginx acts as a reverse proxy, forwarding requests to the Flask app.

### Configuration
Nginx Configuration (`nginx/default.conf`)
The Nginx configuration file sets up a reverse proxy to forward requests to the Flask app:

```
upstream app {
  server app:5000;
}

server {
  listen 80;
  location / {
    proxy_pass http://app;
  }
}
```

### Docker Compose Configuration (`docker-compose.yml`)
The Docker Compose file defines two services: `app` (Flask app) and `nginx`:
```
version: '3'
services:
  app:
    build: ./app
    container_name: app
    restart: always
    # ports:
    #   - '5000:5000'
    expose:
      - 5000

  nginx:
    build: ./nginx
    container_name: nginx
    restart: always
    ports:
      - '80:80'
```

### Customizing the Project
- **Add more routes**: Modify `app/app.py` to add more routes to the Flask app.

- **Change Nginx configuration**: Edit `nginx/default.conf` to customize Nginx behavior.

-- **Add more services**: Extend `docker-compose.yml` to include additional services like databases or caching layers.

### Contributing
If you'd like to contribute to this project, feel free to open an issue or submit a pull request.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

----

### How to Add This to Your GitHub Repository
1. Create a new repository on GitHub.
2. Clone the repository to your local machine:
```
git clone https://github.com/MohammadAminar/FlaskSimpleApp.git
```
3. Copy the project files into the cloned repository.
4. Add the `README.md` file to the root of the repository.
5. Commit and push the changes:
```
git add .
git commit -m "Initial commit"
git push origin main
```
