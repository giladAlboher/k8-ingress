# README - Pepsi and Coca-Cola Deployments on Kubernetes

This repository contains Kubernetes manifests to deploy two simple web services using Nginx serving Pepsi and Coca-Cola messages. The deployment includes two Deployments, two Services, and ConfigMaps to store Nginx configuration for each service.

## Prerequisites

Before deploying these services, ensure you have the following prerequisites:

1. A running Kubernetes cluster.
2. `kubectl` command-line tool installed and configured to access your cluster.

## Deployment

To deploy the Pepsi and Coca-Cola services, follow the steps below:

1. Clone this repository:

```bash
git clone <repository_url>
cd <repository_name>
```

2. Deploy Pepsi service:

```bash
kubectl apply -f pepsi-deployment.yaml
kubectl apply -f pepsi-service.yaml
kubectl apply -f pepsi-conf-configmap.yaml
```

3. Deploy Coca-Cola service:

```bash
kubectl apply -f cola-deployment.yaml
kubectl apply -f cola-service.yaml
kubectl apply -f cola-conf-configmap.yaml
```

4. Verify the deployments:

```bash
kubectl get deployments
kubectl get services
```

## Accessing the Services

After the deployment is successful, you can access the Pepsi and Coca-Cola services using the NodePort of their respective services.

- **Pepsi Service**:
  - To access the Pepsi service, find the NodePort of the `pepsi-service` using the following command:

  ```bash
  kubectl get services pepsi-service
  ```

  - Access the Pepsi service in a web browser using the NodePort, e.g., `http://<node_ip>:<node_port>`.

- **Coca-Cola Service**:
  - To access the Coca-Cola service, find the NodePort of the `cola-service` using the following command:

  ```bash
  kubectl get services cola-service
  ```

  - Access the Coca-Cola service in a web browser using the NodePort, e.g., `http://<node_ip>:<node_port>`.

## Configuration

### Pepsi Deployment

The Pepsi deployment uses the Nginx image `nginx:1.11.5` and mounts the Nginx configuration from the ConfigMap named `pepsi-conf`. The Nginx configuration returns a custom message for the `/` route.

### Coca-Cola Deployment

The Coca-Cola deployment uses the Nginx image `nginx:1.11.5` and mounts the Nginx configuration from the ConfigMap named `cola-conf`. The Nginx configuration returns a custom message for the `/` route.

### ConfigMaps

The ConfigMaps `pepsi-conf` and `cola-conf` store the Nginx configuration for the Pepsi and Coca-Cola services, respectively.

## Clean Up

To remove the deployed resources, run the following commands:

```bash
kubectl delete -f cola-conf-configmap.yaml
kubectl delete -f cola-service.yaml
kubectl delete -f cola-deployment.yaml

kubectl delete -f pepsi-conf-configmap.yaml
kubectl delete -f pepsi-service.yaml
kubectl delete -f pepsi-deployment.yaml
```

Please ensure you back up any important data before running the clean-up commands.

## Disclaimer

This deployment is intended for testing and demonstration purposes. The messages and services are fictional and not affiliated with any brand. In a production environment, make sure to use appropriate configurations and secure the services properly.

## Contributing

If you find any issues with the deployment or want to contribute to the repository, feel free to open a pull request or an issue. Your feedback and contributions are appreciated!
