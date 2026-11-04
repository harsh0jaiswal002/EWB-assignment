# EWB Cybersecurity Assessment 01 — Security Foundations

**Author:** Harsh Jaiswal  
**Program:** EWB AI-Powered Cybersecurity  
**Assessment:** 01 · 100 marks · Issued 18 October 2026

> **Scope:** Educational analysis of fictional scenarios and synthetic logs only. No real websites, accounts, or systems were tested.

## Overview

This repository documents an account-security risk assessment, phishing-message analysis, sign-in alert triage, and critical review of AI-generated security advice.

## Contents

- [Task A — Secure a Student Account](#task-a--secure-a-student-account-25-marks)
- [Task B — Analyse a Suspicious Message](#task-b--analyse-a-suspicious-message-25-marks)
- [Task C — Triage a Sign-in Alert](#task-c--triage-a-sign-in-alert-25-marks)
- [Task D — Review an AI Security Answer](#task-d--review-an-ai-security-answer-25-marks)

---

## Task A — Secure a Student Account (25 marks)

### A1–A2. Five risks, CIA impact, controls and limitations

| Risk | Asset at risk | CIA impact | Practical control | Limitation |
| --- | --- | --- | --- | --- |
| Short password reused for email and portal | Email and learning portal accounts | Confidentiality: both accounts may be accessed if one password is guessed or leaked. Integrity: coursework or messages could be changed. | Use a unique, long password or passphrase for each account, stored in a password manager. | A strong password does not prevent phishing or a stolen authenticated session. |
| Approving unexpected sign-in prompts | Account and MFA protection | Confidentiality and integrity: an attacker with the password may complete login after an accidental approval. | Reject unrequested prompts; report them and use phishing-resistant MFA, such as passkeys, where available. | Even strong MFA cannot stop every type of account or device compromise. |
| Postponed device updates | Laptop, files and sessions | Confidentiality and integrity: known flaws may expose data or permit malware; availability may suffer. | Enable automatic operating-system, browser and application updates. | Updates do not eliminate unknown vulnerabilities or unsafe behaviour. |
| Only project copy on one laptop | Project files | Availability: theft, damage or ransomware could make the only copy unavailable; integrity may also be lost. | Keep versioned backups in a separate trusted location; test restoration. | Backups can be outdated or inaccessible unless regularly checked. |
| Friend uses Mira’s signed-in account | Portal account and personal files | Confidentiality: friend can view private information. Integrity: actions may be wrongly attributed to Mira. | Lock the screen; use separate standard user accounts and sign out of sensitive services. | Separate accounts do not help if Mira shares her password or leaves sessions unlocked. |

### A2. First three actions in priority order

1. Stop approving unexpected MFA requests and review recent sign-ins immediately. This behaviour can directly permit an unauthorised session, so it needs urgent attention.

2. Replace reused passwords with separate strong passwords, starting with email and then the learning portal. Email often controls password-reset links for other services.

3. Create and verify a separate backup of project work. Losing the only copy could permanently interrupt studies. Updates and separate laptop accounts should follow promptly; all five controls matter.

### A3. Authentication versus authorisation

Authentication checks who Mira is. For example, the learning portal checks her password and MFA before signing her in. Authorisation decides what she is allowed to do after login. Mira may view her own grades and upload her assignments, but she should not be able to edit another student’s marks or access an administrator’s settings. A successful login does not give permission to access everything.

## Task B — Analyse a Suspicious Message (25 marks)

### B1. Five warning signs

| Evidence phrase | Why it needs scrutiny |
| --- | --- |
| “awards@campus-awards.example” | The college normally uses campus.example; this is a different domain, not proof of an official scholarship office. |
| “Reply-To: help@personal-awards.example” | Replies are directed to another unrelated domain, which may divert students away from an official channel. |
| “FINAL WARNING - scholarship expires in 20 minutes” | Extreme urgency pressures the recipient to act without checking. |
| “enter your college password and OTP” | The request seeks authentication secrets that could be used to access an account. |
| “Do not contact the college office” and “photo of your identity card” | It discourages independent verification and requests sensitive identity information. |

### B2. Safe verification plan

1. Do not open the message link, reply, send documents or provide an OTP. 2. Open the college portal using a saved bookmark or manually entered official address, not the message link. 3. Contact the scholarship office using contact information obtained independently from the official college website or a known phone number. 4. Ask whether the scholarship and deadline exist; report the suspicious message to the college IT/security team. 5. Retain the original email and headers for authorised review.

HTTPS encrypts a connection but does not prove the website belongs to the college; fraudulent websites can also use HTTPS. A familiar display name can be freely chosen or impersonated, so it is not proof of sender identity.

### B3. Response if the student entered password and OTP

1. Immediately use the independently verified official portal to change the exposed password, and change it on any other account where it was reused. 2. Contact official IT support urgently, report the OTP disclosure and request revocation of active sessions, review of MFA methods and account recovery settings, and temporary restriction if needed. 3. Review recent logins, email forwarding rules, profile changes, sent messages and scholarship/payment details for unauthorised activity. 4. Preserve the suspicious message and relevant timestamps, and monitor the account for further alerts. 5. If an identity card was shared, report that exposure too and follow institutional guidance. Never send the password or OTP to someone claiming to investigate.

### B4. What cannot be established

The text alone cannot prove that the sender controls a malicious website or that anyone has been compromised. Additional evidence would include authenticated email headers, official confirmation from the college, and an authorised security review of the destination and relevant account logs. The .example addresses are fictional training data and must not be visited.

## Task C — Triage a Sign-in Alert (25 marks)

### C1. Four-point timeline

| Time (IST, 18 Oct 2026) | Observed evidence | Interpretation (not proven) |
| --- | --- | --- |
| 09:00–09:01 | Password success and MFA approval from usual classroom egress 192.0.2.10. | Consistent with a normal login, but the logs alone do not identify the user. |
| 10:14–10:16 | Two password failures followed by a success from 198.51.100.23. | Could indicate guessing, a mistyped password or use of a known password. |
| 10:17–10:18 | MFA denied and then approved from 198.51.100.23; student says they approved a prompt to stop repeated requests. | Consistent with MFA prompt fatigue or a mistaken approval; the student denies initiating a login. |
| 10:20 | Session created from 198.51.100.23. | A session was established; the log does not show what the session subsequently did. |

### C2. Likely explanation, alternative and checks

Likely explanation: someone other than the student obtained or guessed the password and repeatedly triggered MFA; the student approved a prompt, allowing a session. This is a plausible account-compromise scenario, not a confirmed attacker identity.

Alternative explanation: a legitimate device or application using a different network retried authentication, and the student misunderstood the source of the prompts. A different IP alone does not establish malicious activity.

Check 1: Correlate sign-in records with device identifiers, browser/user-agent details, session IDs, MFA challenge records and location context, if available. Check 2: Review session activity after 10:20 and independently ask the student to verify their devices and actions. Neither check should assume an IP address identifies a person.

### C3. Three prioritised actions for authorised IT

1. Contain possible access: revoke suspicious sessions/tokens, reset the password through the official process, review MFA registrations and require secure re-authentication. 2. Preserve evidence before routine deletion: export relevant sign-in, MFA and session logs with timestamps and access controls; document actions and maintain an evidence trail. 3. Investigate and recover: review account activity and devices, verify the student’s account changes, monitor for recurrence and educate the student not to approve unexpected prompts.

### C4. Incident summary (60–100 words)

On 18 October 2026, student07 had a normal-looking sign-in at 09:00–09:01 from the usual classroom IP. At 10:14–10:20, a different documentation IP showed two failed passwords, one successful password, an MFA denial, an MFA approval and a created session. The student denies signing in after 09:05 and says they approved a prompt to stop repeated requests. These facts raise concern about MFA fatigue and possible unauthorised access, but do not establish the actor’s identity. Priority is to protect the account, preserve logs and examine subsequent session activity.

## Task D — Review an AI Security Answer (25 marks)

### D1. Five unsafe or unsupported claims and corrections

| Claim/action in fictional AI output | Correction and reasoning |
| --- | --- |
| “The email is safe because it uses HTTPS.” | Incorrect. HTTPS protects data in transit, not the legitimacy of the organisation. The message asks for passwords and OTPs and uses unverified domains. |
| “The sign-in logs prove that the person using 198.51.100.23 stole the password.” | Unsupported. Logs show authentication events from an IP, not a person or how a password was obtained. |
| “MFA prevents every account compromise.” | False. MFA reduces risk, but the scenario shows an unrequested MFA approval can permit a session. |
| “Delete the suspicious logs.” | Unsafe. Preserve relevant logs securely for investigation, accountability and incident reconstruction. |
| “Send the student’s password to support so they can test it.” | Unsafe. Never disclose passwords or OTPs. Official support should use secure resets and authorised log review instead. |

### D2. Improved prompt for an AI tool

“Analyse only the fictional scholarship email and synthetic sign-in logs supplied in EWB Assessment 01. List observed facts separately from hypotheses and unknowns. Identify phishing indicators and possible account-compromise indicators without claiming that an IP identifies a person or that a site is malicious solely because of its URL. Recommend safe verification, evidence preservation and authorised incident-response steps. Do not request, reproduce or handle real passwords, OTPs, identity documents or student personal data. Explain the limitations of your conclusions and cite reliable security guidance for general recommendations.”

### D3. Corrected security advice (100–150 words)

Treat the scholarship message as suspicious, not as confirmed malicious. Its urgent deadline, request for a college password and OTP, and discouragement of official contact are serious warning signs. Do not use the link or send identity documents. Verify any scholarship independently through the college’s official portal or known contact details. HTTPS alone does not establish trust. In the synthetic sign-in logs, a successful password event, MFA approval and session creation from a different IP suggest possible unauthorised access, especially because the student denies initiating the login. However, the logs cannot identify the person or prove how the password was obtained. Authorised IT staff should protect the account, revoke questionable sessions, review MFA settings and preserve evidence. Never delete investigation logs or request a student’s password. AI-generated conclusions must be checked against the actual evidence.

### D4. AI-use declaration and evidence/reference notes

AI-use declaration: OpenAI ChatGPT was used to help draft and organise the written answers, tables and explanations.

Evidence note 1: EWB Assessment 01, pages 2–3: fictional email evidence, reserved example IP addresses, MFA events and the student statement. These support the scenario-specific analysis but not a confirmed attacker identity.

Reference note 2: CISA, “Secure Our World” (https://www.cisa.gov/secure-our-world), provides general guidance on phishing, passwords and MFA. NIST, “AI Risk Management Framework: Generative AI Profile” (NIST AI 600-1, https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf), supports checking generative-AI outputs and acknowledging unreliable or unsupported claims.

---

## Repository files

- `README.md` — GitHub-friendly full report.
- `EWB_Cyber_Assessment01_Harsh_Jaiswal.docx` — editable report for review.
- `original-assessment.pdf` — original assignment instructions.
