# 📈 ms-zipkin

This microservice provides distributed tracing capabilities for the application ecosystem using [Zipkin](https://zipkin.io/). It allows services to collect and visualize trace data to identify latency bottlenecks and understand service dependencies.

---

## 🔗 Project Links

- 📋 [Trello Board](https://trello.com/invite/b/680296aa17864e87fc6c7fed/ATTI82505e108ae3e7a005ede0081ec437f87CDDDEF1/microservice)

---

## 📁 Project Structure

- `Dockerfile`: Based on the official `openzipkin/zipkin` image, with a minor customization to avoid runtime log errors.
- `k8s/deployment.yaml`: Kubernetes deployment manifest with one replica of the Zipkin container.
- `k8s/service.yaml`: Exposes Zipkin via a `LoadBalancer` service on port 9411.
- `.github/workflows/deploy.yaml`: CI/CD pipeline for automated builds and deployment to AKS.
- `.github/workflows/slack.yaml`: Sends Slack notifications on each push to `main`.

---

## 🐳 Docker Image

The image uses the official `openzipkin/zipkin` as base. 

## ☸️ Kubernetes Deployment

- A single pod runs the zipkin container.
- The container listens on port 9411.
- The service is exposed using type: LoadBalancer, so it is accessible from outside the cluster.
---

## 🔁 CI/CD Pipeline

CI/CD is handled by GitHub Actions:

1. The GitHub Actions workflow:
2. Logs into Azure and ACR.
3. Builds and tags the Docker image using the current commit SHA.
4. Pushes the image to Azure Container Registry.
5. Applies the Kubernetes manifests.
6. Updates the image in the Zipkin deployment.
7. Waits for and prints the LoadBalancer IP.

---
## 📢 Slack Integration

A secondary GitHub Actions workflow notifies a Slack channel when changes are pushed to the `main` branch. This helps keep the team informed of updates in the `ms-zipkin` microservice repository.


---


## <b> Made by </b>

+ [Fabiana Valderruten](https://github.com/FFabianna "FFabianna")
+ [Gloria Vicuña](https://github.com/Vanesa155 "Vanesa V.")

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)