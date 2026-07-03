# Helm

**Helm** is the package manager for Kubernetes.

It simplifies application deployment by using **Charts**, which are reusable templates containing Kubernetes resource definitions.

Instead of creating multiple YAML files manually, Helm allows you to deploy applications with a single command.

---

## Why Helm?

Without Helm:

- Multiple YAML files
- Manual updates
- Difficult version management

With Helm:

- One command deployment
- Easy upgrades
- Simple rollbacks
- Reusable templates

---

## Helm Components

| Component | Description |
|----------|-------------|
| Chart | Collection of Kubernetes YAML templates |
| Release | Running instance of a Chart |
| Repository | Collection of Helm Charts |
| Values | Custom configuration for a Chart |

---

## Install Helm

Verify the installation.

```bash
helm version
```

---

## Add a Repository

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```

Update repositories.

```bash
helm repo update
```

---

## Search Charts

Search available charts.

```bash
helm search repo nginx
```

---

## Install a Chart

Install an NGINX chart.

```bash
helm install my-nginx bitnami/nginx
```

---

## View Releases

```bash
helm list
```

---

## Upgrade a Release

```bash
helm upgrade my-nginx bitnami/nginx
```

---

## Rollback a Release

View release history.

```bash
helm history my-nginx
```

Rollback to the previous version.

```bash
helm rollback my-nginx 1
```

---

## Uninstall a Release

```bash
helm uninstall my-nginx
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `helm version` | Display Helm version |
| `helm repo add` | Add a chart repository |
| `helm repo update` | Update repositories |
| `helm search repo` | Search charts |
| `helm install` | Install a chart |
| `helm list` | List releases |
| `helm upgrade` | Upgrade a release |
| `helm history` | View release history |
| `helm rollback` | Roll back a release |
| `helm uninstall` | Remove a release |

---

## Hands-on Exercise

1. Verify Helm installation.
2. Add the Bitnami repository.
3. Update the repository.
4. Search for the NGINX chart.
5. Install the chart.
6. Verify the release.
7. Upgrade the release.
8. Uninstall the release.

---

## Summary

In this chapter, you learned how to:

- Understand Helm
- Add Helm repositories
- Install applications
- Upgrade releases
- Roll back deployments
- Remove Helm releases

---
