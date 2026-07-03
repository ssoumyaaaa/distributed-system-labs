# Services

A **Service** is a Kubernetes resource that provides a stable network endpoint for accessing one or more Pods.

Since Pods are temporary and their IP addresses can change, Services ensure applications remain accessible using a consistent IP address and DNS name.

---

## Why Services?

Without a Service:

```text
Client
   │
   ▼
Pod (10.244.0.5)

Pod Deleted

New Pod (10.244.0.12)

Client Connection Failed
```

With a Service:

```text
          Client
             │
             ▼
      Kubernetes Service
             │
     ┌───────┴────────┐
     ▼                ▼
   Pod-1            Pod-2
```

The Service automatically routes traffic to healthy Pods.

---

## Service Types

| Type | Description |
|------|-------------|
| ClusterIP | Default service, accessible only within the cluster |
| NodePort | Exposes the application on a node port |
| LoadBalancer | Exposes the application using an external load balancer |
| ExternalName | Maps a Service to an external DNS name |

---

## Create a Deployment

```bash
kubectl create deployment nginx \
--image=nginx \
--replicas=3
```

Verify the Pods.

```bash
kubectl get pods
```

---

## Create a ClusterIP Service

Expose the Deployment.

```bash
kubectl expose deployment nginx \
--port=80 \
--target-port=80
```

View the Service.

```bash
kubectl get services
```

Example output:

```text
NAME         TYPE        CLUSTER-IP      PORT(S)
nginx        ClusterIP   10.96.120.200   80/TCP
```

---

## Create a Service Using YAML

Create **nginx-service.yaml**

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  selector:
    app: nginx

  ports:
    - port: 80
      targetPort: 80

  type: ClusterIP
```

Apply the configuration.

```bash
kubectl apply -f nginx-service.yaml
```

---

## Describe a Service

```bash
kubectl describe service nginx-service
```

Displays:

- Cluster IP
- Ports
- Endpoints
- Labels
- Events

---

## Access the Service

Forward the Service port.

```bash
kubectl port-forward service/nginx-service 8080:80
```

Open your browser.

```
http://localhost:8080
```

---

## Create a NodePort Service

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-nodeport

spec:
  selector:
    app: nginx

  ports:
    - port: 80
      targetPort: 80
      nodePort: 30080

  type: NodePort
```

Apply the configuration.

```bash
kubectl apply -f nginx-nodeport.yaml
```

Access the application.

```
http://<Node-IP>:30080
```

---

## View Endpoints

```bash
kubectl get endpoints
```

This shows which Pods receive traffic from the Service.

---

## Delete a Service

```bash
kubectl delete service nginx-service
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get services` | List Services |
| `kubectl describe service` | View Service details |
| `kubectl expose deployment` | Create a Service |
| `kubectl get endpoints` | View Service endpoints |
| `kubectl port-forward service/...` | Access a Service locally |
| `kubectl delete service` | Delete a Service |

---

## Hands-on Exercise

1. Create an Nginx Deployment with **3 replicas**.
2. Expose it using a **ClusterIP** Service.
3. Verify the Service using `kubectl get services`.
4. View the Service details.
5. Access the application using port forwarding.
6. Create a **NodePort** Service.
7. Verify the Service endpoints.
8. Delete both Services.

---

## Summary

In this chapter, you learned how to:

- Understand Kubernetes Services
- Create ClusterIP and NodePort Services
- Expose Deployments
- Access applications through Services
- View Service endpoints
- Delete Services

---
