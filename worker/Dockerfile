FROM python:3.9-slim

WORKDIR /app

# Install system dependencies (needed for PostgreSQL adapter)
RUN apt-get update && apt-get install -y \
    gcc \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip first (VERY IMPORTANT for large wheels like torch)
RUN pip install --upgrade pip

# Copy requirements separately for Docker cache
COPY requirements.txt .

# Install Python dependencies (long timeout for torch)
RUN pip install --no-cache-dir -r requirements.txt --timeout 300

# Copy application code
COPY . .

# Fix for "silent" logs
ENV PYTHONUNBUFFERED=1

CMD ["python", "worker.py"]
