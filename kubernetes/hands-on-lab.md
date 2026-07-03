# Hands-on Lab

In this lab, you'll deploy a simple NGINX application on a Kubernetes cluster and expose it using a Service.

This lab combines the concepts learned throughout this module.

---

## Objective

In this lab, you will learn how to:

- Create a Namespace
- Deploy an application
- Scale a Deployment
- Expose the application using a Service
- Verify Kubernetes resources
- Clean up the cluster

---

## Lab Environment

| Component | Value |
|----------|-------|
| Kubernetes | Kind Cluster |
| Runtime | Podman Desktop / Docker |
| CLI | kubectl |
| Application | NGINX |

---

## Step 1: Create a Namespace

```bash
kubectl create namespace demo
```

Verify.

```bash
kubectl get namespaces
```

---

## Step 2: Create a Deployment

```bash
kubectl create deployment nginx \
--image=nginx \
-n demo
```

Verify.

```bash
kubectl get deployments -n demo
```

---

## Step 3: Scale the Deployment

```bash
kubectl scale deployment nginx \
--replicas=3 \
-n demo
```

Verify.

```bash
kubectl get pods -n demo
```

---

## Step 4: Expose the Deployment

```bash
kubectl expose deployment nginx \
--type=NodePort \
--port=80 \
-n demo
```

Verify.

```bash
kubectl get services -n demo
```

---

## Step 5: Port Forward

```bash
kubectl port-forward service/nginx 8080:80 -n demo
```

Open your browser.

```
http://localhost:8080
```

You should see the **NGINX Welcome Page**.

---

## Step 6: View Resources

View all resources.

```bash
kubectl get all -n demo
```

Describe the Deployment.

```bash
kubectl describe deployment nginx -n demo
```

View Pod logs.

```bash
kubectl logs <pod-name> -n demo
```

---

## Step 7: Delete the Deployment

```bash
kubectl delete deployment nginx -n demo
```

Delete the Service.

```bash
kubectl delete service nginx -n demo
```

Delete the Namespace.

```bash
kubectl delete namespace demo
```

---

## Lab Summary

You successfully learned how to:

- Create a Namespace
- Deploy an application
- Scale a Deployment
- Expose an application
- Verify Kubernetes resources
- Clean up the cluster

---
