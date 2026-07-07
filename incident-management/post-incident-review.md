# Post-Incident Review (PIR)

A Post-Incident Review (PIR) is a structured meeting conducted after a major incident has been resolved. Its purpose is to evaluate how the incident was handled, identify areas for improvement, and reduce the likelihood and impact of similar incidents in the future.

A PIR is a learning exercise focused on improving systems and processes—not assigning blame.

---

## Objectives

- Review the incident from start to finish
- Understand what happened and why
- Evaluate the effectiveness of the response
- Identify process and technical improvements
- Assign action items to prevent recurrence
- Improve operational readiness

---

## When Should a PIR Be Conducted?

A Post-Incident Review is typically conducted after:

- Major Incidents (P1/P2)
- High business impact outages
- SLA breaches
- Recurring incidents
- Security incidents
- Significant production failures

Ideally, the review should be held within a few days of incident resolution while the details are still fresh.

---

## Participants

A PIR may include:

- Incident Manager
- Application Support Team
- Infrastructure Team
- Database Team
- Network Team
- Development Team
- Business Representatives
- Service Owners

Each participant contributes insights from their role during the incident.

---

## PIR Process

```text
Incident Resolved
        │
        ▼
Collect Timeline & Evidence
        │
        ▼
Review Response Activities
        │
        ▼
Discuss Root Cause
        │
        ▼
Identify Improvements
        │
        ▼
Assign Action Items
        │
        ▼
Track Completion
```

---

## Topics to Discuss

During the review, consider the following questions:

- What triggered the incident?
- How was the incident detected?
- Was the incident logged and prioritized correctly?
- Was communication timely and effective?
- Were the right teams involved?
- What worked well?
- What challenges were encountered?
- How can similar incidents be prevented?

---

## Example Timeline Review

| Time | Activity |
|------|----------|
| 09:00 | Monitoring alert received |
| 09:05 | Incident logged |
| 09:10 | Bridge call started |
| 09:25 | Root cause identified |
| 09:45 | Service restored |
| 10:00 | Validation completed |
| 10:15 | Incident closed |

Reviewing the timeline helps identify delays and opportunities for improvement.

---

## Action Items

A PIR should result in measurable actions.

Examples include:

- Improve monitoring and alerting
- Update Standard Operating Procedures (SOPs)
- Enhance application logging
- Increase automated testing
- Improve deployment validation
- Conduct team training
- Update disaster recovery documentation

Each action should have:

- Owner
- Target completion date
- Current status

---

## Sample PIR Summary

| Field | Details |
|--------|---------|
| Incident ID | INC00012345 |
| Service | Online Banking |
| Business Impact | Login service unavailable |
| Root Cause | Database connection pool exhaustion |
| Resolution | Restarted authentication service |
| Lessons Learned | Monitoring thresholds were too high |
| Preventive Actions | Add connection pool alerts and load testing |

---

## Best Practices

- Hold the review soon after the incident.
- Encourage open and honest discussion.
- Focus on improving systems and processes.
- Support conclusions with evidence.
- Document decisions and action items.
- Track preventive actions to completion.

---

## Common Mistakes

- Turning the review into a blame session
- Skipping key stakeholders
- Failing to document lessons learned
- Not assigning owners for action items
- Closing action items without verification

---

## Key Takeaways

- A Post-Incident Review helps organizations learn from incidents and continuously improve.
- The focus should be on identifying process improvements, strengthening systems, and preventing future incidents.
- The success of a PIR is measured by the implementation of meaningful improvements—not just by holding the meeting.
