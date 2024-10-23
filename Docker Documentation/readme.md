# Creating a Docker documentation text file
docker_doc = """
# Docker Documentation

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
   - [System Requirements](#system-requirements)
   - [Installing Docker](#installing-docker)
3. [Docker Architecture](#docker-architecture)
4. [Docker Commands](#docker-commands)
   - [Basic Commands](#basic-commands)
   - [Working with Images](#working-with-images)
   - [Working with Containers](#working-with-containers)
5. [Dockerfile](#dockerfile)
   - [Writing a Dockerfile](#writing-a-dockerfile)
   - [Dockerfile Instructions](#dockerfile-instructions)
6. [Docker Compose](#docker-compose)
7. [Best Practices](#best-practices)
8. [Troubleshooting](#troubleshooting)
9. [Conclusion](#conclusion)

---

## Introduction
Docker is an open-source platform that automates the deployment, scaling, and management of applications using containerization. Containers allow developers to package applications with all dependencies in isolated environments.

## Installation

### System Requirements
- **Supported OS**: Linux, macOS, and Windows.
- **Minimum RAM**: 2GB
- **Processor**: 64-bit architecture

### Installing Docker

#### On Linux (Ubuntu)
```bash
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker