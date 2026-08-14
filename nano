#!/bin/bash

set -e

REPO_DIR="$HOME/DevOps-7Day-Project"
IMAGE_NAME="devops-task3:v1"
CONTAINER_NAME="devops-task7"
HOST_PORT="8084"
CONTAINER_PORT="80"

echo "======================================"
echo "Starting deployment"
echo "======================================"

cd "$REPO_DIR"

echo "[1/5] Pulling latest source code..."
git pull origin main

echo "[2/5] Building Docker image..."
docker build -t "$IMAGE_NAME" -f Docker/Dockerfile .

echo "[3/5] Stopping existing container..."

if docker ps -a --format '{{.Names}}' | grep -q "^${CONTAINER_NAME}$"; then
    docker rm -f "$CONTAINER_NAME"
    echo "Existing container removed."
else
    echo "No existing container found."
fi

echo "[4/5] Starting new container..."

docker run -d \
    --name "$CONTAINER_NAME" \
    -p "$HOST_PORT:$CONTAINER_PORT" \
    --restart unless-stopped \
    "$IMAGE_NAME"

echo "[5/5] Verifying application..."

sleep 3

if curl -f -s "http://localhost:$HOST_PORT" > /dev/null; then
    echo "======================================"
    echo "DEPLOYMENT SUCCESSFUL"
    echo "Application: http://localhost:$HOST_PORT"
    echo "======================================"
else
    echo "======================================"
    echo "DEPLOYMENT FAILED"
    echo "======================================"
    exit 1
fi
