# Use slim variant to reduce base image size
FROM python:3.11-slim-bookworm

# Set working directory
WORKDIR /app

# Install system dependencies and Terraform in a single layer to reduce image size
# Also clean up cache in the same step to keep the layer small
RUN apt-get update && apt-get install -y --no-install-recommends \
    gnupg \
    software-properties-common \
    curl \
    unzip \
    git \
    lsb-release \
    ca-certificates && \
    # Install Terraform
    curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/hashicorp.list && \
    apt-get update && apt-get install -y terraform && \
    # Clean up
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    # Install minimal Python dependencies
    pip install --no-cache-dir requests loguru

# Verify installation (optional - remove if you want to make image even smaller)
RUN terraform --version && git --version
