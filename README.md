# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

## Docker

To run docker containers, you need to download and install Docker Desktop from the [official Docker website](https://www.docker.com/products/docker-desktop).

### Setup Development with Docker

Replace `nginx.conf` with `dev.nginx.conf` order to run the application in development mode.

To run the application in development mode, run the following command in the project root directory:

```bash
docker-compose up --build
```

This command will build and run the frontend, backend, and database containers. 
The frontend will be available at: `http://localhost` 
The backend will be available at: `http://localhost/api`, 
with api docs and redocs available at: `http://localhost/docs`,
and `http://localhost/redoc` respectively.
Also, there is an adminer panel available at: `http://db.localhost` to view the database, and nginx proxy is available at: `http://proxy.localhost` to manage proxy configurations.

### Setup Production with Docker

Replace `nginx.conf` with `prod.nginx.conf` order to run the application in production mode.

To run the application in production mode, run the following command:

```bash
docker-compose -f docker-compose.yml up --build
```

This command will build and run the frontend, backend, and database containers. The frontend will be available at `https://namelesscoin.wtf` and the backend will be available at `https://namelesscoin.wtf/api`, with api docs and redocs available at `https://namelesscoin.wtf/docs` and `https://namelesscoin.wtf/redoc` respectively.

Also, there is an adminer panel available at `http://db.namelesscoin.wtf` to view the database, and nginx proxy is available at `http://proxy.namelesscoin.wtf` to manage proxy configurations.

### Setup with another domain

To use new domain, we need to create a new SSL certificate, you can use the following command, via removing 443 ports on `production.nginx.conf`, via replacing `{domain.name}` with your domain name.

```bash
docker compose up -d
docker-compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d {domain.name}
```

and change the domain name in `production.nginx.conf` and `docker-compose.yml` files.
