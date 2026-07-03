# Jobs and CronJobs

Kubernetes **Jobs** and **CronJobs** are used to run tasks that eventually complete.

- **Job** → Runs a task once.
- **CronJob** → Runs a task on a schedule.

---

## Why Jobs?

Unlike Deployments, Jobs are designed for short-lived tasks such as:

- Database backup
- Data migration
- Report generation
- Batch processing

---

## Job vs CronJob

| Resource | Purpose |
|----------|---------|
| Job | Runs a task once |
| CronJob | Runs a task on a schedule |

---

## Create a Job

Create **job.yaml**

```yaml
apiVersion: batch/v1
kind: Job

metadata:
  name: hello-job

spec:
  template:
    spec:
      containers:
      - name: hello
        image: busybox
        command: ["echo", "Hello Kubernetes"]

      restartPolicy: Never
```

Create the Job.

```bash
kubectl apply -f job.yaml
```

---

## View Jobs

```bash
kubectl get jobs
```

View Pods created by the Job.

```bash
kubectl get pods
```

---

## Create a CronJob

Create **cronjob.yaml**

```yaml
apiVersion: batch/v1
kind: CronJob

metadata:
  name: hello-cron

spec:
  schedule: "*/2 * * * *"

  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox
            command: ["echo", "Hello Kubernetes"]

          restartPolicy: Never
```

This runs every **2 minutes**.

Create the CronJob.

```bash
kubectl apply -f cronjob.yaml
```

---

## View CronJobs

```bash
kubectl get cronjobs
```

View Jobs created by the CronJob.

```bash
kubectl get jobs
```

---

## Delete Resources

Delete the Job.

```bash
kubectl delete job hello-job
```

Delete the CronJob.

```bash
kubectl delete cronjob hello-cron
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get jobs` | List Jobs |
| `kubectl get cronjobs` | List CronJobs |
| `kubectl describe job` | View Job details |
| `kubectl describe cronjob` | View CronJob details |
| `kubectl apply -f` | Create a Job/CronJob |
| `kubectl delete job` | Delete a Job |
| `kubectl delete cronjob` | Delete a CronJob |

---

## Hands-on Exercise

1. Create a Job.
2. Verify it completes successfully.
3. Create a CronJob.
4. Verify scheduled Jobs are created.
5. Delete the Job.
6. Delete the CronJob.

---

## Summary

In this chapter, you learned how to:

- Create Kubernetes Jobs
- Create CronJobs
- Run one-time tasks
- Schedule recurring tasks
- Manage batch workloads

---
