<div align="center">

# osTicket: From Intake to Resolution

### Help Desk Operations · Ticket Documentation · Security-Aware Support

A documented support workflow following a laptop issue through assignment, investigation, communication, and closure.

[View My Portfolio](https://github.com/jmccuf) · [Project Repository](https://github.com/jmccuf/ticket-lifecycle)

</div>

![Illustrated ticket lifecycle: intake, triage, assignment, investigation, verification, and closure](images/ticket-lifecycle.svg)

> **Evidence and scope:** The screenshots below come from the original repository and show a historical lab ticket. They document a reported laptop power issue, agent assignment, a note reporting battery replacement, and closure with the status “Resolved.” They do not independently prove the physical repair or show requester confirmation. The additional checklists and cybersecurity scenarios are recommended practice, not claims of completed testing.

## Project Overview

This lab demonstrates how a help desk records a request, establishes ownership, communicates progress, and preserves a resolution history using **osTicket**. The example follows ticket **#431007**, titled **“Laptop wont turn on.”**

The original ticket thread shows:

1. A requester reports that a laptop will not power on despite charging.
2. Justin acknowledges the request and coordinates a handoff to Level I Support.
3. The ticket is assigned to a support agent.
4. The agent records a battery issue and reports a replacement.
5. The ticket is closed with a **Resolved** status and appears in the closed-ticket queue.

**Why this matters for cybersecurity:** Accurate ticket ownership, timestamps, escalation, and documented actions also support security operations. This is a help desk lab demonstrating transferable workflow skills—not a completed security incident investigation.

## Environment & Software

| Component | Role in the original lab |
| :--- | :--- |
| osTicket | Ticket creation, assignment, thread history, responses, and closure |
| Microsoft Azure Virtual Machines | Hosting environment identified in the original documentation |
| Internet Information Services (IIS) | Windows web-service environment identified in the original documentation |
| Remote Desktop | Remote access to the Windows lab environment |
| Windows 10 21H2 | Historical lab operating system |

For a new deployment, use supported software and operating systems, confirm current osTicket prerequisites, and follow your organization's access policies. This guide starts with a functioning osTicket installation; it is not an installation tutorial.

## Before Starting

- Confirm that the osTicket user and agent portals are accessible in the lab.
- Create test requester and agent accounts; avoid real customer information.
- Configure appropriate departments, teams, roles, help topics, and SLA plans.
- Use a standard agent account for routine work and an administrator account only when needed.
- Check how your installation handles public replies, internal notes, notifications, custom statuses, and reopening.
- Keep the VM administration interface private where possible. Restrict any temporary public RDP access to a trusted source; never allow it from the entire internet.

> **Terminology:** A lifecycle diagram describes work stages, not a mandatory sequence of osTicket status labels. Status names and queue behavior depend on configuration. “Answered” and “Overdue” are not necessarily mutually exclusive lifecycle stages. Deletion or purging is not a normal substitute for resolving a request.

## 1. Intake — Record the Problem

Create a ticket through the configured user portal or as an authorized agent. Email intake is another option only when mail handling has been configured. Ticket filters can route or act on incoming tickets; they are not required for a ticket to exist.

Capture enough context to support a useful first response:

| Field | Example for this lab |
| :--- | :--- |
| Subject | Laptop will not power on |
| Reported symptom | No power after attempting to charge |
| Affected service or device | Requester's laptop; use a lab asset identifier if available |
| Business impact | Requester cannot work on the affected device |
| Help topic | Personal Computer Issues, as shown in the screenshot |
| Ownership | Assign to the responsible support team or agent |
| Sensitive information | Never request passwords, recovery codes, or tokens in the ticket |

**Good intake questions:** When did the problem start? Is anyone else affected? What safe steps have already been attempted? Is an approved replacement device available?

Do not assume a hardware issue is a cybersecurity incident. Record the symptoms first and escalate only when the evidence and policy justify it.

## 2. Triage & Assignment — Establish Ownership

![Original ticket thread showing the laptop issue, SLA information, acknowledgement, and Level I Support assignment](images/ticket-queue.png)

*Original lab screenshot: ticket #431007 with its help topic, Default SLA, due date, requester message, acknowledgement, and support handoff. Historical account names and timestamps remain visible.*

### What to do

1. Read the request and check for related or duplicate tickets.
2. Assess impact and urgency using the organization's priority policy; a hardware category alone does not determine severity.
3. Select the appropriate help topic and department.
4. Confirm the applicable SLA and due date. The screenshot shows **Default SLA**; it does not demonstrate multiple severity-based SLA plans.
5. Assign an owner or team and record the reason for the handoff.
6. Acknowledge receipt with a clear next step.

**Example response — suggested wording, not copied from the ticket:**

> Thank you for reporting the issue. We have assigned your request to Level I Support for inspection. Please follow the approved device drop-off process. We will update this ticket once the initial assessment is complete. Do not include your password in any reply.

Assignment, department access, and role permissions work together. Confirm who can view or modify the ticket rather than assuming assignment alone defines all access.

## 3. Investigation & Communication — Keep a Useful Record

![Original ticket thread showing agent assignment, a battery-replacement note, and closure with Resolved status](images/ticket-response.png)

*Original lab screenshot: the assigned agent reports a battery replacement, followed by acknowledgement and a closure event. This records the reported outcome; it is not independent hardware-repair evidence.*

### Recommended workflow

1. Review the existing thread before repeating troubleshooting.
2. Record observations separately from assumptions.
3. Document each authorized troubleshooting action and its result.
4. Use **internal notes** for staff-only coordination where appropriate, and **public replies** for requester-facing updates. Verify the selected action before submitting.
5. Check recipients and collaborators before sharing information.
6. Escalate when the issue exceeds the agent's authority or expertise, and record who owns the next action.

### Suggested investigation note

```text
Observation:
The requester reports that the laptop does not power on.

Checks performed:
[Record the safe, authorized checks actually performed.]

Finding:
[Record evidence supporting the diagnosis; avoid speculation.]

Action taken:
[Describe the approved repair or next step.]

Validation:
[Record functional checks and requester confirmation, if obtained.]

Next owner / update:
[Name the responsible role and the next update time.]
```

Internal notes are not a secret vault. Do not store credentials or unnecessary personal data in them, and do not assume they are excluded from every export or integration.

## 4. Resolution & Closure — Verify Before Closing

![Original osTicket closed queue showing the laptop ticket and its closure timestamp](images/ticket-closure.png)

*Original lab screenshot: the ticket appears in the closed queue. This demonstrates recorded closure, not requester confirmation or an independently measured service improvement.*

Before closing a new practice ticket:

- Summarize the reported issue and the action actually taken.
- Record the validation performed and any outstanding limitation.
- Seek requester confirmation when required by your closure policy.
- Confirm there is no unassigned follow-up work.
- Select the appropriate configured resolved/closed status.
- Preserve the thread according to retention policy; do not delete the ticket merely to clear a queue.

**Suggested closure note:**

```text
Reported issue: Laptop would not power on.
Action recorded: [Approved repair or remediation actually performed.]
Validation: [Test performed and observed result.]
Requester confirmation: [Received / pending / not required under policy.]
Follow-up: [None, or link/reference to an assigned follow-up.]
Closure basis: [Why closure is appropriate under the support policy.]
```

The historical thread reports a battery replacement and shows closure. Explicit requester acceptance is not visible, so this guide does not claim it occurred.

## 5. Reopening & Follow-Up

If the issue recurs, follow the configured reopening policy. A reply to a closed ticket may reopen it, remain associated without reopening, or be handled differently depending on configuration and status settings. Test the behavior in your own lab rather than assuming it.

Recommended follow-up:

1. Link the new information to the existing ticket when appropriate.
2. Reassess impact, priority, ownership, and SLA handling.
3. Distinguish the recurring symptom from a new issue.
4. Record why the ticket was reopened and what will change in the investigation.

## Security-Aware Support Practices

![Illustration of security-aware ticket handling: minimize data, control access, escalate carefully, preserve records](images/security-handoff.svg)

These are recommended practices to extend the lab—not controls proven by the original screenshots.

| Practice | How to apply it |
| :--- | :--- |
| Least privilege | Give agents only the access required for their role; test access with permitted and restricted accounts. |
| Identity verification | Follow an approved verification process before password resets, access changes, or sensitive disclosures. |
| Data minimization | Record relevant facts without passwords, MFA codes, unnecessary personal data, or confidential exports. |
| Safe attachments | Do not open suspicious files on the help desk workstation; use the approved security analysis process. |
| Security escalation | Route suspected compromise to the designated security team, preserving timestamps and references. |
| Record preservation | Keep relevant evidence in an approved restricted store; a ticket thread alone is not a forensic evidence system. |

## Suggested Cybersecurity Practice Scenarios

**Planned exercises only.** Use fictional accounts, sanitized artifacts, and an isolated lab. Do not claim these are completed until evidence is added.

| Scenario | Practice objective | Evidence to add |
| :--- | :--- | :--- |
| Suspicious-email report | Record metadata and safely route the report without opening a suspect attachment. | Sanitized intake, escalation note, and assigned owner |
| Account lockout with suspicious activity | Distinguish routine support from potential compromise and verify identity before account changes. | Verification checklist, escalation rationale, and authorized actions |
| Unauthorized software report | Capture the asset reference, reported behavior, and approved escalation path. | Ticket history and security-team handoff |
| Restricted ticket access | Verify that a permitted agent can access a ticket and an unrelated restricted account cannot. | Sanitized positive and negative access-test results |

## Evidence & Validation Checklist

### Visible in the original screenshots

- [x] Requester describes a laptop power issue.
- [x] Ticket metadata includes a help topic, SLA plan, and due date.
- [x] Support assignment and agent communication are recorded.
- [x] A note reports battery replacement.
- [x] Closure with a Resolved status and a closed-queue entry are shown.

### Additional checks to perform

- [ ] Verify requester-facing versus internal-note visibility.
- [ ] Confirm expected agent permissions with positive and negative access tests.
- [ ] Record functional validation and requester acceptance where required.
- [ ] Test reopening behavior under the actual configuration.
- [ ] Complete a clearly labeled cybersecurity practice scenario.
- [ ] Review all screenshots for personal information before republishing.

## Skills Demonstrated

**Documented:** ticket ownership, support communication, assignment handoffs, resolution notes, and tracking a request through closure.

**Recommended next steps:** access-control testing, security escalation exercises, requester confirmation, and evidence-handling procedures. No production deployment, security certification, or quantified service improvement is claimed by this lab.

## Screenshot & Diagram Notes

The three PNG screenshots were retrieved from this repository's original README and visually reviewed for accurate captions. They retain the original lab account names and timestamps; confirm you are comfortable publishing those details or redact them before upload. The two SVG diagrams are newly created explanatory illustrations, not screenshots of osTicket or proof of new testing. All images are stored locally in `images/` so the README does not depend on older repository attachment URLs.

---

**[Back to my cybersecurity portfolio](https://github.com/jmccuf)**
<br />
