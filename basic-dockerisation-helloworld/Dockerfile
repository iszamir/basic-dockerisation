#Lightweight Python base image
FROM python:3.9-slim

# Set working directory
WORKDIR /app

#Copy only necessary files
COPY app.py .
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Run as non root user
RUN useradd -m myuser && chown -m myuser  /app
USER myser

#Health check (optional)
HEALTHCHECK --interval=30s --timeout=3s \
CMD python -c "import requests; requests.get('http://localhost:8080/health', timeout=2) || exit 1

# Run the application
CMD ["python", "app.py"]
