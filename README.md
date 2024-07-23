# Camunda Prometheus Exporter

[![Maven Central](https://img.shields.io/maven-central/v/io.camunda/zeebe-process-test-root)](https://search.maven.org/search?q=g:io.camunda%20zeebe-process-test)

## Introduction

The Camunda Prometheus Exporter app returns metric values for the count of Docker image pulls in a DockerHub organization, running in a Kubernetes cluster. The app exposes these metrics via a Prometheus-compatible endpoint.

## Prerequisites

Ensure you have the following tools installed:

- Docker 25.0.0+
- kubectl 1.29+
- kind 0.21.0
- GNU Make 3.81+
- bash 4.2+
- curl 8.6.0+
- Coreutils binaries (on Linux)

## Exporter App

The Prometheus Exporter app performs the following functions:

- Runs on port 2113
- Accepts the environment variable `DOCKERHUB_ORGANIZATION` to specify the DockerHub organization name
- On a GET request to `/metrics`, it returns the list of gauge metric values `docker_image_pulls` for each public Docker image in the specified organization, with the values representing the number of DockerHub image pulls.

## Setup Instructions

### Dependency

Install the required Python dependencies listed in `requirements.txt`:

```plaintext
prometheus-client==0.15.0
requests==2.28.2
