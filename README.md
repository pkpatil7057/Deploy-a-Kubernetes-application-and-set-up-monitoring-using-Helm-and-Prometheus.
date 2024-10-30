# Kubernetes Cluster Setup with Monitoring

## Project Overview
Deploy a sample app on Kubernetes and set up monitoring with Prometheus and Grafana using Helm charts.

## Technologies
- Kubernetes
- Helm
- Prometheus
- Grafana

## Setup
1. **Install Minikube or connect to a Kubernetes cluster.**
   - For Minikube, follow the [Minikube installation guide](https://minikube.sigs.k8s.io/docs/start/).
   - Start Minikube with:
     ```bash
     minikube start
     ```

2. **Deploy Prometheus and Grafana using Helm.**
   - Add the Prometheus community helm repo:
     ```bash
     helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
     helm repo update
     ```
   - Install Prometheus:
     ```bash
     helm install prometheus prometheus-community/prometheus
     ```
   - Install Grafana:
     ```bash
     helm install grafana grafana/grafana
     ```

3. **Deploy the sample app with `kubectl apply`.**
   - Navigate to the `k8s` directory:
     ```bash
     cd k8s
     ```
   - Apply the deployment and service:
     ```bash
     kubectl apply -f deployment.yaml
     kubectl apply -f service.yaml
     ```

## Monitoring
Prometheus will scrape metrics, and Grafana will visualize them. Access Grafana by port-forwarding:
```bash
kubectl port-forward service/grafana 3000:80
