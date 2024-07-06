# Use an official Python runtime as a parent image
FROM python:3.10-slim

# Set environment variables to avoid potential Python issues
ENV PYTHONUNBUFFERED 1

# Install dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends curl gcc libpq-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -
ENV PATH="/root/.local/bin:$PATH"

# Set the working directory to /app
WORKDIR /app

# Copy only the necessary files
COPY pyproject.toml poetry.lock /app/

# Install Python dependencies using Poetry
RUN poetry install --no-dev 

# Copy the rest of the application
COPY . /app

# Expose the port FastAPI is running on
EXPOSE 8000

# Run the prestart script to initialize the database
CMD poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000
