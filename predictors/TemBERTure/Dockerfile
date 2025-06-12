# Use CUDA 11.3 base image which is compatible with PyTorch 1.10.2
FROM nvidia/cuda:11.3.1-base-ubuntu20.04

# Avoid timezone interactive prompt during installation
ENV DEBIAN_FRONTEND=noninteractive 

# Set working directory
WORKDIR /app

# Install system dependencies and Python 3.9
RUN apt update && apt install -y \
    python3 \
    python3-pip \
    git \
    && rm -rf /var/lib/apt/lists/*

# Clone TemBERTure repository
RUN git clone https://github.com/Protein-sequence-embeddings/temBERTure.git /app/temBERTure

# Install Python dependencies
RUN pip3 install --no-cache-dir -r /app/temBERTure/requirements.txt

# Set environment variables
ENV PYTHONPATH=/app

# Set working directory to TemBERTure
WORKDIR /app/temBERTure

# Set the entrypoint
CMD ["python3", "-c", "print('TemBERTure container ready. Use: docker run -v /path/to/data:/input -v /path/to/output:/output protscout:temberture python temBERTure.py')"]