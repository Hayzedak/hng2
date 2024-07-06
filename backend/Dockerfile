# Backend Dockerfile

# Use the official Python image from the Docker Hub
FROM python:3.10-slim AS base

# Set the working directory
WORKDIR /app

# Install Poetry
RUN pip install poetry

# Copy only the requirements to cache them in docker layer
COPY poetry.lock pyproject.toml /app/

# Install dependencies
RUN poetry config virtualenvs.create false && poetry install --no-dev

# Copy the rest of the application
COPY . /app

# Run the application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]

