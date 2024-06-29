FROM python:3.10-slim

# Adding backend directory to make absolute filepaths consistent across services
WORKDIR /app/backend

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt /app/backend/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy project files
COPY . /app/backend/

# Set up entrypoint script
RUN ["chmod", "+x", "/app/backend/entrypoint.sh"]
ENTRYPOINT ["/app/backend/entrypoint.sh"]

# Expose the application port
EXPOSE 8000
