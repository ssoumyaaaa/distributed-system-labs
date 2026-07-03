# ConfigMaps

A **ConfigMap** is a Kubernetes resource used to store non-sensitive configuration data as key-value pairs.

Instead of hardcoding configuration inside a container image, ConfigMaps allow you to externalize configuration and update it without rebuilding the application.

> **Note:** Store passwords, tokens, and API keys in **Secrets**, not ConfigMaps.

---

## Why ConfigMaps?

Without ConfigMaps:

- Configuration is hardcoded
- Requires rebuilding images for every change
- Difficult to manage across environments

With ConfigMaps:

- External configuration
- Easy updates
- Reusable across multiple Pods
- Better application portability

---

## ConfigMap Architecture

```text
          ConfigMap
      +----------------+
      | APP_ENV=dev    |
      | PORT=8080      |
      +-------+--------+
              |
              |
      +-------v--------+
      |      Pod       |
      |   Application  |
      +----------------+
```

---

## Create a ConfigMap

Create a ConfigMap using the command line.

```bash
kubectl create configmap app-config \
--from-literal=APP_NAME=DemoApp \
--from-literal=APP_ENV=Development
```

---

## View ConfigMaps

```bash
kubectl get configmaps
```

Example output:

```text
NAME         DATA   AGE
app-config   2      20s
```

---

## Describe a ConfigMap

```bash
kubectl describe configmap app-config
```

---

## Create a ConfigMap Using YAML

Create **configmap.yaml**

```yaml
apiVersion: v1
kind: ConfigMap

metadata:
  name: app-config

data:
  APP_NAME: DemoApp
  APP_ENV: Development
  PORT: "8080"
```

Apply the configuration.

```bash
kubectl apply -f configmap.yaml
```

---

## Use ConfigMap as Environment Variables

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx

    envFrom:
    - configMapRef:
        name: app-config
```

Apply the Pod.

```bash
kubectl apply -f nginx-pod.yaml
```

---

## Verify Environment Variables

```bash
kubectl exec nginx-pod -- env
```

Example output:

```text
APP_NAME=DemoApp
APP_ENV=Development
PORT=8080
```

---

## Update a ConfigMap

Edit the ConfigMap.

```bash
kubectl edit configmap app-config
```

Or update using YAML.

```bash
kubectl apply -f configmap.yaml
```

> **Note:** Existing Pods may need to be restarted to pick up updated environment variables.

---

## Delete a ConfigMap

```bash
kubectl delete configmap app-config
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl create configmap` | Create a ConfigMap |
| `kubectl get configmaps` | List ConfigMaps |
| `kubectl describe configmap` | View ConfigMap details |
| `kubectl edit configmap` | Edit a ConfigMap |
| `kubectl apply -f` | Create or update from YAML |
| `kubectl delete configmap` | Delete a ConfigMap |

---

## Hands-on Exercise

1. Create a ConfigMap named **app-config**.
2. Verify the ConfigMap.
3. Create an Nginx Pod that uses the ConfigMap.
4. Verify the environment variables inside the Pod.
5. Update the ConfigMap.
6. Restart the Pod.
7. Verify the updated configuration.
8. Delete the ConfigMap.

---

## Summary

In this chapter, you learned how to:

- Understand ConfigMaps
- Create ConfigMaps
- Use ConfigMaps in Pods
- Store application configuration
- Update ConfigMaps
- Delete ConfigMaps

---
