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

## Docker Setup Guide

This guide will help you run your application using Docker, whether for development or production environments.

### Prerequisites

Ensure you have Docker Desktop installed. You can download it from the [official Docker website](https://www.docker.com/products/docker-desktop).

### Development Setup

To set up the development environment, follow these steps:

1. **Replace Nginx Configuration**:
   - Replace `nginx.conf` with `dev.nginx.conf`.

2. **Build and Run Containers**:
   - Navigate to the project root directory and run:
     ```bash
     docker-compose up --build
     ```

3. **Access the Application**:
   - **Frontend**: [http://localhost](http://localhost)
   - **Backend**: [http://localhost/api](http://localhost/api)
   - **API Docs**: [http://localhost/docs](http://localhost/docs)
   - **ReDoc**: [http://localhost/redoc](http://localhost/redoc)
   - **Adminer Panel**: [http://db.localhost](http://db.localhost)
   - **Nginx Proxy Manager**: [http://proxy.localhost](http://proxy.localhost)

### Production Setup

To set up the production environment, follow these steps:

1. **Replace Nginx Configuration**:
   - Replace `nginx.conf` with `prod.nginx.conf`.

2. **Build and Run Containers**:
   - Run the following command:
     ```bash
     docker-compose -f docker-compose.yml up --build
     ```

3. **Access the Application**:
   - **Frontend**: [https://namelesscoin.wtf](https://namelesscoin.wtf)
   - **Backend**: [https://namelesscoin.wtf/api](https://namelesscoin.wtf/api)
   - **API Docs**: [https://namelesscoin.wtf/docs](https://namelesscoin.wtf/docs)
   - **ReDoc**: [https://namelesscoin.wtf/redoc](https://namelesscoin.wtf/redoc)
   - **Adminer Panel**: [http://db.namelesscoin.wtf](http://db.namelesscoin.wtf)
   - **Nginx Proxy Manager**: [http://proxy.namelesscoin.wtf](http://proxy.namelesscoin.wtf)

### Using a Custom Domain

To set up the application with a custom domain:

1. **Create a New SSL Certificate**:
   - Remove the 443 ports from `production.nginx.conf`.
   - Replace `{domain.name}` with your domain name in the following command:
     ```bash
     docker compose up -d
     docker-compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d {domain.name}
     ```

2. **Update Configuration Files**:
   - Change the domain name in both `production.nginx.conf` and `docker-compose.yml` files.

### Additional Notes

- Ensure you have the correct permissions to run Docker commands.
- Verify that all services are running correctly after executing the `docker-compose up` command.
- For more detailed information on each service, refer to the corresponding documentation in your project.

By following these steps, you can easily set up and run your application in both development and production environments using Docker.
