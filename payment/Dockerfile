# Use latest stable Python version
FROM python:3.12-slim

# Optional: Install system dependencies (for uWSGI)
RUN apt-get update && \
    apt-get install -y build-essential python3-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set environment variables
ENV INSTANA_SERVICE_NAME=payment \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Create app directory
WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy app files
COPY *.py ./
COPY payment.ini ./

# Port the service will listen on
EXPOSE 8080

# Optional: If you added a non-root user, you could switch to it here
# RUN useradd -m appuser && chown -R appuser /app
# USER appuser

# Start with uWSGI using the ini config
CMD ["uwsgi", "--ini", "payment.ini"]
