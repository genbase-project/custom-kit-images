FROM python:3.11-slim

LABEL maintainer="Utkarsh Kanwat <utkarshkanwat@gmail.com>"
LABEL description="Custom image with Python and Git"

# Prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install Git and common dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Verify installations
RUN python --version && pip --version && git --version

# Set up working directory
WORKDIR /app

# Set default Python path
ENV PYTHONPATH="/app:${PYTHONPATH}"

# Set Git configurations globally
RUN git config --global user.name "Utkarsh Kanwat" && \
    git config --global user.email "utkarshkanwat@gmail.com"

# Optional: Install common Python packages
# RUN pip install numpy pandas matplotlib requests

# Default command when container starts
CMD ["bash"]
