# Secrets

A **Secret** is a Kubernetes resource used to store sensitive information such as passwords, API keys, tokens, and certificates.

Unlike ConfigMaps, Secrets are designed to handle confidential data and can be consumed by Pods as environment variables or mounted files.

> **Note:** Secrets are Base64 encoded by default. They are **not encrypted** unless encryption at rest is enabled in the Kubernetes cluster.

---

## Why Secrets?

Without Secrets:

- Passwords are hardcoded
- Credentials are stored in YAML files
- Sensitive data is exposed

With Secrets:

- Secure storage for sensitive data
- Separate configuration from application code
- Reusable across multiple Pods
- Easy credential management

---

## Secret Architecture

```text
             Secret
      +--------------------+
      | USERNAME=admin     |
      | PASSWORD=******    |
      +---------+----------+
                |
                |
        +-------v--------+
        |      Pod       |
        |  Application   |
        +----------------+
```

---

## Create a Secret

Create a Secret using the command line.

```bash
kubectl create secret generic app-secret \
--from-literal=USERNAME=admin \
--from-literal=PASSWORD=Password123
```

---

## View Secrets

```bash
kubectl get secrets
```

Example output:

```text
NAME         TYPE      DATA   AGE
app-secret   Opaque    2      15s
```

---

## Describe a Secret

```bash
kubectl describe secret app-secret
```

> Secret values are not displayed for security reasons.

---

## Create a Secret Using YAML

Encode the values using Base64.

```bash
echo -n admin | base64
echo -n Password123 | base64
```

Example output:

```text
YWRtaW4=
UGFzc3dvcmQxMjM=
```

Create **secret.yaml**

```yaml
apiVersion: v1
kind: Secret

metadata:
  name: app-secret

type: Opaque

data:
  USERNAME: YWRtaW4=
  PASSWORD: UGFzc3dvcmQxMjM=
```

Apply the configuration.

```bash
kubectl apply -f secret.yaml
```

---

## Use a Secret as Environment Variables

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx

    env:
    - name: USERNAME
      valueFrom:
        secretKeyRef:
          name: app-secret
          key: USERNAME

    - name: PASSWORD
      valueFrom:
        secretKeyRef:
          name: app-secret
          key: PASSWORD
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
USERNAME=admin
PASSWORD=Password123
```

---

## Delete a Secret

```bash
kubectl delete secret app-secret
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl create secret generic` | Create a Secret |
| `kubectl get secrets` | List Secrets |
| `kubectl describe secret` | View Secret details |
| `kubectl apply -f` | Create a Secret from YAML |
| `kubectl delete secret` | Delete a Secret |

---

## Hands-on Exercise

1. Create a Secret named **app-secret**.
2. Verify the Secret.
3. Create a Pod that uses the Secret.
4. Verify the environment variables inside the Pod.
5. Delete the Pod.
6. Delete the Secret.

---

## Best Practices

- Never store passwords in ConfigMaps.
- Avoid committing Secret YAML files to Git.
- Use strong, unique credentials.
- Enable encryption at rest in production clusters.
- Rotate Secrets regularly.

---

## Summary

In this chapter, you learned how to:

- Understand Kubernetes Secrets
- Create Secrets using commands and YAML
- Use Secrets in Pods
- Store sensitive information securely
- Follow Secret management best practices

---
