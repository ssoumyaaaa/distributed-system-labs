# Ingress

An **Ingress** is a Kubernetes resource that manages external HTTP and HTTPS access to applications running inside a cluster.

Instead of exposing every application using a **NodePort** or **LoadBalancer**, an Ingress provides a single entry point and routes traffic to different Services based on rules.

> **Note:** An Ingress requires an **Ingress Controller** (such as NGINX Ingress Controller) to function.

---

## Why Ingress?

Without Ingress:

```text
Client
   │
   ├── NodePort (App 1)
   ├── NodePort (App 2)
   └── NodePort (App 3)
```

With Ingress:

```text
             Client
                │
                ▼
        Ingress Controller
                │
      ┌─────────┴─────────┐
      ▼                   ▼
 Service A           Service B
      │                   │
      ▼                   ▼
    Pods                Pods
```

One endpoint can route traffic to multiple applications.

---

## Benefits of Ingress

- Single entry point
- URL-based routing
- Host-based routing
- SSL/TLS termination
- Load balancing
- Reduced number of exposed ports

---

## Install NGINX Ingress Controller

For a Kind cluster:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

Verify the controller.

```bash
kubectl get pods -n ingress-nginx
```

---

## Create a Deployment

```bash
kubectl create deployment nginx \
--image=nginx \
--replicas=2
```

Expose it as a Service.

```bash
kubectl expose deployment nginx \
--port=80
```

---

## Create an Ingress

Create **ingress.yaml**

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress

metadata:
  name: nginx-ingress

spec:
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix

        backend:
          service:
            name: nginx
            port:
              number: 80
```

Apply the configuration.

```bash
kubectl apply -f ingress.yaml
```

---

## Verify the Ingress

```bash
kubectl get ingress
```

Example output:

```text
NAME            CLASS   HOSTS   ADDRESS
nginx-ingress   nginx   *       localhost
```

Describe the Ingress.

```bash
kubectl describe ingress nginx-ingress
```

---

## Host-Based Routing

Example:

```yaml
rules:
- host: app.example.com

  http:
    paths:
    - path: /
      pathType: Prefix

      backend:
        service:
          name: nginx
          port:
            number: 80
```

Traffic to `app.example.com` is routed to the **nginx** Service.

---

## Path-Based Routing

Example:

```yaml
rules:
- http:
    paths:

    - path: /app1
      pathType: Prefix

      backend:
        service:
          name: app1-service
          port:
            number: 80

    - path: /app2
      pathType: Prefix

      backend:
        service:
          name: app2-service
          port:
            number: 80
```

Requests are routed based on the URL path.

---

## Delete the Ingress

```bash
kubectl delete ingress nginx-ingress
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get ingress` | List Ingress resources |
| `kubectl describe ingress` | View Ingress details |
| `kubectl apply -f` | Create an Ingress |
| `kubectl delete ingress` | Delete an Ingress |
| `kubectl get pods -n ingress-nginx` | Verify the Ingress Controller |

---

## Hands-on Exercise

1. Install the NGINX Ingress Controller.
2. Create an Nginx Deployment.
3. Expose it using a Service.
4. Create an Ingress resource.
5. Verify the Ingress.
6. Access the application through the Ingress.
7. Delete the Ingress resource.

---

## Summary

In this chapter, you learned how to:

- Understand Kubernetes Ingress
- Install an Ingress Controller
- Create an Ingress resource
- Configure host-based routing
- Configure path-based routing
- Route external traffic to Services

---
