# Kubernetes Quick Deploy Samples

This repository hosts minimal Kubernetes manifests for deploying an NGINX workload. Publish this repository to GitHub so the manifests can be fetched directly via their raw URLs.

## Repository layout

```
k8s/
├── nginx-deployment.yaml
└── nginx-service.yaml
```

- `k8s/nginx-deployment.yaml` creates a `Deployment` with two NGINX pods, readiness and liveness probes, and resource limits.
- `k8s/nginx-service.yaml` exposes the deployment internally with a `ClusterIP` `Service` on port 80.

## Instant deployment instructions

Follow these steps once this repository is available on GitHub.

1. **Connect kubectl to a cluster.** Make sure `kubectl config current-context` shows the cluster you plan to use (for example, Minikube or a managed Kubernetes service).
2. **Open the raw manifest.** Navigate to the manifest in GitHub (e.g., `k8s/nginx-deployment.yaml`), click **Raw**, and copy the URL. A published repository named `K8s` under your account would have a link such as:
   ```
   https://raw.githubusercontent.com/<your-username>/K8s/main/k8s/nginx-deployment.yaml
   ```
3. **Apply the manifest.** Run the command with the raw URL:
   ```bash
   kubectl apply -f https://raw.githubusercontent.com/<your-username>/K8s/main/k8s/nginx-deployment.yaml
   ```
   Repeat for other manifests (such as the service) if needed.
4. **Verify the resources.** Confirm the objects were created:
   ```bash
   kubectl get all -l app=nginx
   ```

### Testing suggestions

- Use a local cluster like Minikube: `minikube start` followed by the apply commands above.
- Or use an online Kubernetes playground that allows `kubectl` access; paste the same commands into the terminal.

Kubernetes will create the deployment, pods, and service defined in the YAML files when you run `kubectl apply`. Feel free to fork and adapt the manifests for your own workloads.
