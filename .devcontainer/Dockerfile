FROM python:3.12-slim

RUN apt-get update && apt-get install -y \
    curl \
    git \
    git-lfs \
    libgl1 \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

RUN git lfs install --system

RUN curl -LsSf https://astral.sh/uv/install.sh | sh

ENV PATH="/root/.local/bin:$PATH"

WORKDIR /app

# Creación del entorno virtual con tu nomenclatura
RUN uv venv .Joshee

COPY requirements.txt .

# Instalación de dependencias en el entorno virtual
RUN uv pip install --python .Joshee/bin/python -r requirements.txt

# Activación global del entorno virtual para el contenedor
ENV VIRTUAL_ENV=/app/.Joshee
ENV PATH="/app/.Joshee/bin:$PATH"