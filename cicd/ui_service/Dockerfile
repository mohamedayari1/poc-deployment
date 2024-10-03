# Use the official Python image with version 3.10
FROM python:3.10-slim AS base

# Set working directory
WORKDIR /app

# Install Poetry
RUN pip install --no-cache-dir poetry

# Copy dependency files
COPY pyproject.toml poetry.lock* /app/

# Install dependencies
RUN poetry install --only main

# Copy the application code from the ui_service directory
COPY . /app/

# Expose the port Streamlit is running on
EXPOSE 8500

# Run Streamlit when the container launches
CMD ["poetry", "run", "streamlit", "run", "app.py", "--server.port=8500", "--server.address=0.0.0.0"]
