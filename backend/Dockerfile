# Use the official Python image from the Docker Hub
FROM python:3.10-slim as build

# Set the working directory
WORKDIR /app

# Install Poetry and dependencies
COPY pyproject.toml poetry.lock ./
RUN pip install poetry \
    && poetry config virtualenvs.create false \
    && poetry install --no-dev

# Copy the rest of the application code
COPY . .

# Command to run the application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]

