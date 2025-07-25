FROM ghcr.io/astral-sh/uv:python3.10-bookworm-slim

# Need git and build-essential (provides gcc compiler) for pre-commit, also libgl1 for object detection
RUN apt update -y \
 && apt install git -y \
 && apt install build-essential -y

# These are for object detection
RUN apt install libgl1 -y \
 && apt install libglib2.0-0 -y

# This is for document prediction
RUN sudo apt install tesseract-ocr -y

# Create a user with a given User and Group ID
# https://vsupalov.com/docker-shared-permissions/
ARG UID
ARG GID
RUN addgroup --gid $GID user
RUN adduser --disabled-password --gecos '' --uid $UID --gid $GID user

SHELL ["/bin/bash", "--login", "-c"]

USER user
