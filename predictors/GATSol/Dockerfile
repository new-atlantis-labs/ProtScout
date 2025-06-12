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

# Create placeholder directory (repository not available)
RUN mkdir -p /app/GATSol
RUN echo "# GATSol repository not available" > /app/GATSol/README.md

# Install common Python dependencies for protein analysis
RUN pip install --no-cache-dir \
    numpy \
    pandas \
    torch \
    torch-geometric \
    scikit-learn

# Set torch cache dir for esm weitghts
RUN mkdir -p /root/.cache/torch/hub/checkpoints && \
    chmod -R 777 /root/.cache

# Set working directory to GATSol
WORKDIR /app/GATSol

# Default command to run predictions
CMD ["python", "-c", "print('GATSol container ready. Use: docker run -v /path/to/data:/input -v /path/to/output:/output protscout:gatsol python predict.py')"]