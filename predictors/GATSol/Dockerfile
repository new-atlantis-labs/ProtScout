# Use CUDA-enabled PyTorch base image
FROM pytorch/pytorch:2.2.2-cuda11.8-cudnn8-runtime

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    make \
    gcc \
    g++ \
    pkg-config \
    freetype* \
    libpng-dev \
    && rm -rf /var/lib/apt/lists/*

# Clone GATSol repository
RUN apt-get update && apt-get install -y git && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/ningyu-wang/GATSol.git /app/GATSol

# Install Python dependencies
RUN pip install --no-cache-dir -r /app/GATSol/requirements.txt

# Set torch cache dir for esm weitghts
RUN mkdir -p /root/.cache/torch/hub/checkpoints && \
    chmod -R 777 /root/.cache

# Set working directory to GATSol
WORKDIR /app/GATSol

# Default command to run predictions
CMD ["python", "-c", "print('GATSol container ready. Use: docker run -v /path/to/data:/input -v /path/to/output:/output protscout:gatsol python predict.py')"]