# Week 4, Docker Compose with PostgreSQL, then Kubernetes (k3s)

## What this does
Runs the incident tracker and a PostgreSQL database. Originally built as a two-service Compose stack with a named volume; the Compose stack is now stopped and the app runs on a single-node k3s Kubernetes cluster.

## Requirements
- k3s (kubectl)
- A `.env` file in `week-4/` (copy `.env.example` and fill in real values)
- The `week-4-web` image imported into k3s's containerd

## Run it
```bash
kubectl create secret generic db-credentials --from-env-file=.env
kubectl apply -f env-configmap.yaml -f db-data-persistentvolumeclaim.yaml -f db-service.yaml -f db-deployment.yaml -f web-service.yaml -f web-deployment.yaml
kubectl port-forward --address 0.0.0.0 service/web 8080:8080
```

Compose is stopped; Kubernetes is now how this app actually runs.

## Verify
```bash
kubectl get pods
kubectl get svc
```
Or visit http://localhost:8080 in a browser while port-forward is running.

## Running with Compose instead (original setup)
```bash
docker compose up -d --build
docker compose down
```
Add `-v` to `down` only if you want to delete the database volume.
