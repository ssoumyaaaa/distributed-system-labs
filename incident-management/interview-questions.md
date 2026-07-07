# Incident Management Interview Questions

This document contains commonly asked interview questions on Incident Management for Technology Support, Application Support, Production Support, and Operations roles.

---

## Beginner Level

### 1. What is an incident?

**Answer:**

An incident is an unplanned interruption to an IT service or a reduction in its quality. The primary objective of Incident Management is to restore normal service as quickly as possible while minimizing business impact.

---

### 2. What is Incident Management?

**Answer:**

Incident Management is the process of identifying, logging, analyzing, resolving, and closing incidents to restore normal business operations within agreed Service Level Agreements (SLAs).

---

### 3. What is the goal of Incident Management?

**Answer:**

The goal is to restore service quickly, minimize business disruption, meet SLA commitments, and maintain customer satisfaction.

---

### 4. What is the difference between an Incident and a Problem?

**Answer:**

| Incident | Problem |
|----------|---------|
| Unplanned interruption to a service | The underlying cause of one or more incidents |
| Focuses on restoring service | Focuses on preventing recurrence |
| Requires immediate attention | May be investigated after service restoration |

---

### 5. What is the difference between Priority and Severity?

**Answer:**

- **Severity** measures the technical impact of an incident.
- **Priority** determines how urgently the incident should be resolved based on business impact and urgency.

---

## Intermediate Level

### 6. What are the stages of the Incident Lifecycle?

**Answer:**

1. Detection
2. Logging
3. Categorization
4. Prioritization
5. Assignment
6. Investigation
7. Escalation
8. Resolution
9. Validation
10. Closure

---

### 7. What information should be included in an incident ticket?

**Answer:**

- Incident ID
- Date and time
- Affected application
- Description of the issue
- Business impact
- Priority and Severity
- Error messages
- Resolution steps
- Current status

---

### 8. When should an incident be escalated?

**Answer:**

An incident should be escalated when:

- Specialized expertise is required
- SLA is at risk
- Business impact increases
- Multiple teams are involved
- Initial troubleshooting does not resolve the issue

---

### 9. What is a Major Incident?

**Answer:**

A Major Incident is a high-impact incident that significantly affects business operations and requires immediate coordination, frequent communication, and rapid service restoration.

---

### 10. What is a bridge call?

**Answer:**

A bridge call (also called a war room) is a dedicated meeting where all relevant technical and business teams collaborate in real time to resolve a major incident.

---

## Advanced Level

### 11. What is Root Cause Analysis (RCA)?

**Answer:**

Root Cause Analysis is the process of identifying the underlying cause of an incident so that corrective and preventive actions can be implemented to avoid recurrence.

---

### 12. What is a Post-Incident Review (PIR)?

**Answer:**

A Post-Incident Review is a structured meeting conducted after a major incident to review the timeline, analyze the response, identify lessons learned, and assign improvement actions.

---

### 13. What is the difference between Corrective Action and Preventive Action?

**Answer:**

| Corrective Action | Preventive Action |
|-------------------|-------------------|
| Resolves the current issue | Prevents similar incidents in the future |
| Immediate fix | Long-term improvement |

---

### 14. What is an SLA?

**Answer:**

A Service Level Agreement (SLA) is a formal agreement that defines the expected response and resolution times for incidents based on their priority.

---

### 15. How do you handle a P1 production incident?

**Answer:**

A typical approach is:

1. Acknowledge the incident immediately.
2. Assess business impact.
3. Declare a Major Incident if required.
4. Start a bridge call.
5. Engage the required technical teams.
6. Communicate regularly with stakeholders.
7. Restore service as quickly as possible.
8. Validate the solution.
9. Complete RCA and a Post-Incident Review.

---

## Scenario-Based Questions

### 16. A production application is down. What would you do first?

**Answer:**

- Confirm the outage.
- Check monitoring dashboards.
- Verify server and application health.
- Log or review the incident ticket.
- Assess business impact.
- Notify stakeholders if necessary.
- Begin troubleshooting or escalate to the appropriate team.

---

### 17. A service restart fixes the issue. Is the incident complete?

**Answer:**

No. While the service has been restored, the incident should be validated, documented, and followed by Root Cause Analysis if appropriate.

---

### 18. What would you do if the incident is close to breaching its SLA?

**Answer:**

- Escalate immediately.
- Notify the Incident Manager.
- Update stakeholders.
- Involve additional technical teams if needed.
- Continue troubleshooting until resolution.

---

### 19. Why is documentation important during an incident?

**Answer:**

Documentation provides a record of the investigation, supports communication, assists Root Cause Analysis, improves future troubleshooting, and satisfies audit requirements.

---

### 20. What qualities make a good Application Support Engineer during an incident?

**Answer:**

- Strong troubleshooting skills
- Clear communication
- Calm under pressure
- Good documentation
- Collaboration across teams
- Understanding of SLAs
- Ability to prioritize effectively
- Commitment to continuous learning

---

## Quick Revision

| Topic | Key Point |
|--------|-----------|
| Incident | Unplanned service disruption |
| Priority | Business urgency |
| Severity | Technical impact |
| SLA | Response and resolution targets |
| RCA | Identify the underlying cause |
| PIR | Review and improve after an incident |
| Major Incident | High-impact service disruption |
| Escalation | Transfer to the appropriate team or management level |

---
