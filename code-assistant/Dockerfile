# Use a Debian-based Python image that includes common tools or makes installation easier
FROM python:3.11-bookworm

# Set working directory
WORKDIR /app

# Install system dependencies required by aider (specifically git)
# Update package lists, install git, then clean up apt lists to keep image small
RUN apt-get update && \
    apt-get install -y --no-install-recommends git && \
    rm -rf /var/lib/apt/lists/*

# Install wheel first to support building packages with pyproject.toml
RUN pip install --upgrade pip wheel setuptools

# Install Python dependencies: aider-chat and gitpython
# Use --no-cache-dir to reduce layer size
RUN pip install --no-cache-dir "aider-chat>=0.40.0" "gitpython>=3.1.0"

# (Optional) Add a default command for manual debugging if needed
CMD ["/bin/bash"]
