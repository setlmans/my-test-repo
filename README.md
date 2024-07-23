# Camunda Prometheus Exporter 

## Introduction

The Camunda Prometheus Exporter app returns metric values for the count of Docker image pulls in a DockerHub organization. The app is implemented in Python and runs in a Docker container with adjustments for Kubernetes clusters.

## Prerequisites

Ensure you have the following tools installed:

- Python 3.12+
- Docker 25.0.0+
- bash 4.2+
- Coreutils binaries (on Linux)

## Exporter App

The Prometheus Exporter app performs the following functions:

- Runs on port 2113 by default and accepts the environment variable `PORT`
- In order to specify the DockerHub organization name the app accepts the environment variable `DOCKERHUB_ORGANIZATION` 
- On a GET request to `/metrics`, it returns the list of gauge metric values `docker_image_pulls` for each public Docker image in the specified organization, with the values representing the number of DockerHub image pulls.

## Setup Instructions

### Building and Running with Docker

You need to have internet access in order to download the base Python image from the docker hub

To build and run the Docker container:

```plaintext
docker build -t camunda-prometheus-exporter .
docker run -p 2113:2113 camunda-prometheus-exporter

# Usage

Once the application is running, you can access the metrics at 
http://localhost:2113/metrics
