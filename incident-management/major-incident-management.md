# Major Incident Management (MIM)

A **Major Incident** is a high-impact incident that causes significant disruption to critical business services and requires immediate attention, rapid coordination, and continuous communication.

The objective of Major Incident Management is to restore normal service as quickly as possible while minimizing business impact.

---

## What is a Major Incident?

A Major Incident is typically characterized by:

- Critical business service outage
- Large number of users affected
- High financial or operational impact
- Risk of SLA breach
- Immediate management attention required

Examples include:

- Online banking application unavailable
- E-commerce website down during a sale
- Database failure affecting multiple applications
- Complete network outage
- Cloud infrastructure failure
- Authentication service unavailable

---

## Major Incident Lifecycle

```text
Major Incident Detected
          │
          ▼
Incident Declared
          │
          ▼
Incident Manager Assigned
          │
          ▼
Bridge Call Initiated
          │
          ▼
Technical Investigation
          │
          ▼
Regular Stakeholder Updates
          │
          ▼
Service Restored
          │
          ▼
Monitoring & Validation
          │
          ▼
Incident Closed
          │
          ▼
Post-Incident Review (PIR)
```

---

## Roles and Responsibilities

### Incident Manager

Responsible for coordinating the entire incident.

Responsibilities include:

- Declare the Major Incident
- Start the bridge call
- Coordinate technical teams
- Track progress
- Communicate with stakeholders
- Ensure timely resolution

---

### Technical Teams

Examples:

- Application Support
- Linux Team
- Database Team
- Network Team
- Middleware Team
- Cloud Team

Responsibilities:

- Investigate the issue
- Share findings
- Implement recovery actions
- Validate the solution

---

### Business Stakeholders

Responsibilities:

- Assess business impact
- Communicate with business users
- Approve critical business decisions if required

---

## Bridge Call (War Room)

A bridge call is a dedicated meeting where all required teams collaborate to resolve the incident.

Typical participants:

- Incident Manager
- Application Support
- Infrastructure Team
- Database Team
- Network Team
- Cloud Team
- Business Representatives

The bridge remains active until service is restored.

---

## Communication During a Major Incident

Communication should include:

- Current status
- Impact
- Investigation progress
- Estimated time to restore (if available)
- Next update time

Example update:

```
Current Status:
Database connectivity issue identified.

Impact:
Online payments unavailable.

Action:
Database team is restoring the primary database.

Next Update:
15 minutes.
```

---

## Typical Response Timeline

| Time | Activity |
|------|----------|
| 09:00 | Major Incident detected |
| 09:03 | Incident declared |
| 09:05 | Incident Manager assigned |
| 09:07 | Bridge call started |
| 09:15 | Technical investigation |
| 09:40 | Root cause identified |
| 09:50 | Service restored |
| 10:00 | Validation completed |
| 10:15 | Incident closed |

---

## Common Recovery Actions

Depending on the issue, recovery actions may include:

- Restarting failed services
- Rolling back a deployment
- Restoring database connectivity
- Scaling infrastructure
- Switching to a backup server
- Restoring cloud resources
- Reconfiguring network routes

The focus is on restoring service quickly. A permanent fix can be implemented later if necessary.

---

## Success Criteria

A Major Incident is considered resolved when:

- Services are restored
- Users can access the application
- Monitoring shows healthy status
- Stakeholders are informed
- Incident documentation is complete

---

## Best Practices

- Declare a Major Incident early when required.
- Assign clear ownership.
- Keep communication regular and factual.
- Record all major decisions.
- Focus on restoring service before investigating long-term fixes.
- Involve the right teams as early as possible.
- Conduct a Post-Incident Review after resolution.

---

## Common Mistakes

- Delaying the declaration of a Major Incident
- Inviting unnecessary participants to the bridge call
- Poor communication with stakeholders
- Failing to document actions taken
- Closing the incident without validation
- Skipping the Post-Incident Review

---

## Example Scenario

**Incident**

Customers cannot complete online payments.

**Investigation**

- Application team checks logs.
- Database team verifies database health.
- Network team confirms connectivity.
- Root cause identified as a failed database cluster node.

**Resolution**

- Database failover is initiated.
- Application connectivity is restored.
- Users successfully complete transactions.
- Monitoring confirms normal system health.

---

## Key Takeaways

- Major Incident Management focuses on restoring critical business services as quickly as possible.
- Effective coordination, communication, and teamwork are essential.
- The priority is service restoration, followed by root cause analysis and continuous improvement through a Post-Incident Review.
