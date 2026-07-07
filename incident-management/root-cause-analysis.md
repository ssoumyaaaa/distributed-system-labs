# Root Cause Analysis (RCA)

Root Cause Analysis (RCA) is the process of identifying the underlying cause of an incident rather than just resolving its symptoms.

The objective of RCA is to prevent the same incident from occurring again by implementing permanent corrective and preventive actions.

---

## Why is RCA Important?

Performing RCA helps organizations to:

- Prevent recurring incidents
- Improve system reliability
- Reduce downtime
- Enhance customer satisfaction
- Identify process improvements
- Meet compliance and audit requirements

---

## When is RCA Required?

RCA is typically performed for:

- Major Incidents (P1)
- Repeated incidents
- High business impact outages
- Security incidents
- SLA breaches
- Significant production failures

---

## RCA Process

```text
Incident Occurs
        │
        ▼
Service Restored
        │
        ▼
Collect Evidence
        │
        ▼
Analyze Root Cause
        │
        ▼
Identify Corrective Actions
        │
        ▼
Implement Preventive Actions
        │
        ▼
Review & Close
```

---

## Information to Collect

Before beginning the analysis, gather:

- Incident ID
- Timeline
- Error logs
- Monitoring alerts
- Screenshots
- System metrics
- Deployment history
- Configuration changes
- User reports

Accurate data leads to accurate analysis.

---

## Root Cause Analysis Techniques

### 1. Five Whys

Ask **"Why?"** repeatedly until the underlying cause is identified.

### Example

**Problem**

Application is unavailable.

**Why?**

Application service stopped.

**Why?**

The server ran out of memory.

**Why?**

A memory leak caused excessive memory usage.

**Why?**

The application version contained a software defect.

**Why?**

The defect was not detected during testing.

**Root Cause**

Insufficient testing allowed a memory leak to reach production.

---

### 2. Fishbone (Ishikawa) Analysis

This method groups possible causes into categories.

Common categories include:

- People
- Process
- Technology
- Infrastructure
- Network
- Database
- Environment

This technique is useful when multiple contributing factors exist.

---

## Corrective vs Preventive Actions

### Corrective Action

Fixes the immediate issue.

Examples:

- Restart a failed service
- Restore database connectivity
- Roll back a deployment

---

### Preventive Action

Reduces the likelihood of recurrence.

Examples:

- Improve monitoring
- Add automated health checks
- Increase test coverage
- Implement deployment validation
- Update operational procedures

---

## Example RCA

### Incident

Customers could not log in to the application.

### Root Cause

The authentication service failed because its database connection pool was exhausted.

### Resolution

The authentication service was restarted and database connections were restored.

### Preventive Action

- Increase connection pool monitoring.
- Configure connection timeout alerts.
- Optimize database connection management.
- Conduct load testing before future releases.

---

## RCA Report Template

| Field | Description |
|--------|-------------|
| Incident ID | Unique ticket number |
| Date & Time | Incident occurrence |
| Service | Affected application or system |
| Business Impact | Users or services affected |
| Root Cause | Underlying reason for the incident |
| Resolution | Steps taken to restore service |
| Corrective Actions | Immediate fixes |
| Preventive Actions | Long-term improvements |
| Owner | Responsible team |
| Status | Open or Closed |

---

## Best Practices

- Focus on facts, not assumptions.
- Identify the underlying cause, not just the symptom.
- Avoid assigning blame to individuals.
- Support findings with evidence.
- Document all actions and decisions.
- Track preventive actions until completion.

---

## Common Mistakes

- Stopping the investigation too early
- Assuming the first issue found is the root cause
- Blaming individuals instead of improving processes
- Ignoring monitoring or log data
- Failing to implement preventive actions

---

## Interview Questions

### What is Root Cause Analysis?

Root Cause Analysis is a structured process used to identify the underlying reason for an incident so that permanent corrective and preventive actions can be implemented.

---

### Why is RCA important?

RCA helps prevent recurring incidents, improves system reliability, reduces downtime, and supports continuous improvement.

---

### What is the difference between corrective and preventive actions?

- **Corrective Action** resolves the current incident.
- **Preventive Action** reduces the chance of the same incident occurring again.

---

## Key Takeaways

- RCA focuses on identifying and eliminating the underlying cause of incidents.
- Effective RCA relies on evidence, structured analysis, and collaboration across teams.
- Corrective actions restore service, while preventive actions improve long-term stability.
- A well-documented RCA helps organizations learn from incidents and strengthen operational resilience.
