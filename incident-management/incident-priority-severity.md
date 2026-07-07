# Incident Priority vs Severity

Priority and Severity are two key attributes used to classify incidents. Although they are closely related, they represent different aspects of an incident and should not be used interchangeably.

---

## What is Severity?

**Severity** measures the technical impact of an incident on the application or IT service.

It answers the question:

> **How badly is the system affected?**

Severity is determined by the extent of the technical issue, regardless of business urgency.

### Severity Levels

| Severity | Description |
|-----------|-------------|
| Sev 1 | Complete service outage or critical system failure |
| Sev 2 | Major functionality unavailable |
| Sev 3 | Partial loss of functionality |
| Sev 4 | Minor issue with little technical impact |

---

## What is Priority?

**Priority** determines how quickly an incident should be addressed.

It answers the question:

> **How urgently should the incident be resolved?**

Priority is based on business impact and urgency.

### Priority Levels

| Priority | Description | Typical Response |
|-----------|-------------|------------------|
| P1 | Critical | Immediate |
| P2 | High | As soon as possible |
| P3 | Medium | Standard SLA |
| P4 | Low | Planned resolution |

---

## Severity vs Priority

| Severity | Priority |
|-----------|----------|
| Measures technical impact | Measures business urgency |
| Focuses on system health | Focuses on business impact |
| Determined by technical teams | Determined by business impact and support teams |
| Indicates how serious the issue is | Indicates how quickly it must be resolved |

---

## Examples

### Example 1

A banking application is completely unavailable for all customers.

**Severity:** Sev 1

**Priority:** P1

Reason:

- Complete service outage
- Large business impact
- Immediate action required

---

### Example 2

The HR portal is unavailable, but only after office hours.

**Severity:** Sev 1

**Priority:** P3

Reason:

- Technically critical
- Low immediate business impact

---

### Example 3

Only one user cannot log in due to an incorrect account configuration.

**Severity:** Sev 4

**Priority:** P4

Reason:

- Minimal technical impact
- Affects only one user

---

### Example 4

The payment gateway is slow during a major online sale.

**Severity:** Sev 2

**Priority:** P1

Reason:

- Service is still available
- High business impact due to revenue loss

---

## How Priority is Determined

Support teams typically consider:

- Number of affected users
- Business impact
- Service criticality
- Regulatory or compliance requirements
- Financial impact
- Customer impact
- SLA commitments

---

## Priority Matrix

| Business Impact | Urgency | Priority |
|-----------------|---------|----------|
| High | High | P1 |
| High | Medium | P2 |
| Medium | Medium | P3 |
| Low | Low | P4 |

---

## Best Practices

- Do not assume a high severity incident always has the highest priority.
- Consider both technical impact and business impact before assigning a priority.
- Reassess priority if the situation changes.
- Clearly document the reason for the assigned priority and severity.
- Follow organizational SLAs when determining response times.

---

## Interview Questions

### Q1. What is the difference between Priority and Severity?

**Answer:**

Severity measures the technical impact of an incident, while Priority determines how urgently it should be resolved based on business impact and urgency.

---

### Q2. Can a Sev 1 incident have a P3 priority?

**Answer:**

Yes. For example, if a critical internal application fails outside business hours and no users are affected immediately, the technical severity is high, but the business urgency may be lower.

---

### Q3. Who decides Priority?

**Answer:**

Priority is typically decided by the Service Desk or Incident Manager in consultation with business stakeholders and technical teams.

---

## Key Takeaways

- **Severity = Technical Impact**
- **Priority = Business Urgency**
- Priority and Severity are related but independent.
- Correct classification helps ensure incidents are handled according to business needs and SLA commitments.
