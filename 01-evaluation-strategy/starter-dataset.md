# Email Summary Quality Evaluation Dataset

This dataset contains 20 synthetic examples for evaluating the quality of email summaries, plus 2 real outputs added during curation (rows 21 and 22). Each row pairs an input email with a candidate summary, a first-pass `good` or `bad` label, and a one-line justification.

## Dataset

| # | Input email | Candidate summary | First-pass label | One-line reason |
|---:|---|---|:---:|---|
| 1 | **Subject: Project kickoff moved**<br><br>Hi team,<br><br>Our Atlas project kickoff has moved from Tuesday, March 12 at 10:00 a.m. to Wednesday, March 13 at 2:00 p.m. The meeting will still be in Conference Room B, and the agenda is unchanged. Please update your calendars.<br><br>Thanks,<br>Maya | The Atlas kickoff is now Wednesday, March 13 at 2:00 p.m. in Conference Room B; the agenda is unchanged. | good | Concise and faithful: it captures the new date, time, location, and unchanged agenda. |
| 2 | **Subject: Invoice 4821 due Friday**<br><br>Hello Jordan,<br><br>This is a reminder that invoice 4821 for $3,750 is due this Friday, April 19. Please reply if you need another copy of the invoice or expect a delay.<br><br>Best,<br>Accounts Receivable | Invoice 4821 for $3,500 is overdue and must be paid immediately to avoid a late fee. | bad | It changes the amount, says the invoice is already overdue, and invents a late-fee warning. |
| 3 | **Subject: Password reset completed**<br><br>Hi Priya,<br><br>Your company account password was successfully reset at 9:42 a.m. today. If you did not request this change, contact the security desk at extension 4400 immediately.<br><br>IT Support | Priya’s password was reset at 9:42 a.m.; she should call extension 4400 immediately if she did not request it. | good | It preserves both the completed action and the conditional security instruction without adding details. |
| 4 | **Subject: Service interruption update**<br><br>Customers are currently unable to export PDF reports. The engineering team has identified the cause and is testing a fix. We will send another update by 4:00 p.m. UTC. Other reporting features remain available. | The reporting outage has been fully resolved, and all features are working normally. | bad | It falsely claims resolution even though the fix is still being tested and only PDF exports are affected. |
| 5 | **Subject: Your Berlin travel itinerary**<br><br>Hi Elena,<br><br>Your flight to Berlin departs JFK on May 6 at 6:30 p.m. and arrives at BER on May 7 at 8:25 a.m. Your hotel is the Linden Hotel, with check-in after 3:00 p.m. The booking references are attached.<br><br>Travel Desk | Elena flies from JFK to Berlin on May 6 at 6:30 p.m., arrives May 7 at 8:25 a.m., and can check in at the Linden Hotel after 3:00 p.m. | good | It accurately captures the essential flight and hotel details while omitting only nonessential attachment information. |
| 6 | **Subject: PTO request for June 3–5**<br><br>Hi Marcus,<br><br>I’d like to request PTO from Monday, June 3 through Wednesday, June 5. I have asked Lena to cover the Tuesday client call, and I will finish the monthly report before I leave.<br><br>Regards,<br>Devon | Devon is taking the entire first week of June off, has cancelled the client call, and will complete the monthly report after returning. | bad | It expands the leave dates and reverses both the coverage plan and report timing. |
| 7 | **Subject: Shipment delayed by one day**<br><br>Hello,<br><br>Your order #A10493 was delayed because of severe weather. It is now expected to arrive on Thursday, August 22 instead of Wednesday, August 21. No action is required.<br><br>Customer Care | Order #A10493 is delayed by one day and is now expected Thursday, August 22; no action is needed. | good | It states the correct order, revised delivery date, delay length, and action status. |
| 8 | **Subject: Security review required**<br><br>Hi Lee,<br><br>We detected three unsuccessful login attempts from an unfamiliar device. Your account was not accessed, but we have temporarily locked it as a precaution. Use the secure link in the employee portal to verify your identity and unlock the account.<br><br>Security Team | Lee’s account was compromised through an unfamiliar device, and all company data may have been stolen. | bad | It turns unsuccessful attempts into a confirmed breach and invents possible data theft. |
| 9 | **Subject: Volunteer day registration**<br><br>Team,<br><br>Registration is open for our volunteer day at Riverside Food Bank on Saturday, September 14 from 9:00 a.m. to 1:00 p.m. Please register by September 6 using the form on the intranet. Transportation will be provided from the main office.<br><br>People Team | Volunteer day is September 14, 9:00 a.m.–1:00 p.m., at Riverside Food Bank; register on the intranet by September 6, with transport available from the main office. | good | It includes the event, schedule, location, registration deadline, and transport detail accurately. |
| 10 | **Subject: Updated expense policy**<br><br>Starting October 1, receipts will be required for all expenses over $25. Employees must submit expenses within 30 days of purchase. Managers will continue to approve reports in the existing system. | Employees should note that the company has made several general improvements to its expense process, which managers will continue to handle in the usual way. | bad | It is vague and omits both actionable policy changes: the $25 receipt threshold and 30-day deadline. |
| 11 | **Subject: Interview feedback requested**<br><br>Hi panel,<br><br>Please enter your interview feedback for Samir Patel in Greenhouse by noon tomorrow. Focus on the role competencies and avoid discussing compensation; recruiting will handle that separately.<br><br>Thanks,<br>Nora | The panel should submit competency-based feedback for Samir Patel in Greenhouse by noon tomorrow and leave compensation to recruiting. | good | It preserves the deadline, system, feedback focus, and compensation boundary. |
| 12 | **Subject: Annual subscription renewal**<br><br>Dear customer,<br><br>Your Pro plan will renew automatically on November 30 for $240 plus applicable tax. To change or cancel the plan, visit Billing Settings before November 29.<br><br>Support Team | The Pro plan has been cancelled and a $240 refund will be issued on November 30. | bad | It invents a cancellation and refund when the email says the plan will renew automatically. |
| 13 | **Subject: Office closed Monday**<br><br>Colleagues,<br><br>The Toronto office will be closed on Monday, February 17 for Family Day. The building will reopen Tuesday at 8:00 a.m. Employees scheduled to work Monday should work remotely unless their manager has approved time off.<br><br>Facilities | The Toronto office is closed Monday, February 17, reopening Tuesday at 8:00 a.m.; scheduled employees should work remotely unless leave is approved. | good | It accurately summarizes the closure, reopening, and remote-work instruction. |
| 14 | **Subject: Contract comments needed**<br><br>Hi Ana,<br><br>I attached the revised vendor agreement. Please review sections 4 and 7 and send comments by 5:00 p.m. Thursday. Legal has already approved the data-protection language in section 9, so no further review is needed there.<br><br>Owen | Ana must review the entire agreement, especially section 9, and return comments by Friday morning. | bad | It changes the review scope and deadline and incorrectly reopens an already approved section. |
| 15 | **Subject: Damaged item in order 7718**<br><br>Hello support,<br><br>The ceramic lamp in order 7718 arrived with a cracked base. The shade and bulb are fine. I would prefer a replacement lamp rather than a refund. Photos of the damage are attached.<br><br>Thank you,<br>Rina | Rina reports a cracked lamp base in order 7718 and requests a replacement rather than a refund; photos are attached. | good | It captures the damaged item, order number, preferred remedy, and evidence accurately. |
| 16 | **Subject: Version 4.2 release tonight**<br><br>Team,<br><br>Version 4.2 will deploy tonight between 11:00 p.m. and midnight UTC. Users may experience up to five minutes of downtime. The release adds bulk tagging and fixes the dashboard filter bug. No database migration is required.<br><br>Engineering | Tonight, in the late-evening period beginning at 11:00 p.m. and potentially lasting until the clock reaches midnight in Coordinated Universal Time, the engineering organization intends to carry out the deployment of software version 4.2. During that deployment, it is possible that users of the product could encounter a temporary interruption in service lasting as long as approximately five minutes. Among the noteworthy contents of this version are a new capability for applying tags in bulk and a correction for the previously observed dashboard-filter problem. The team also wishes to clarify that this work will not require a database migration. | bad | Although accurate, it is needlessly verbose and largely restates the full email instead of summarizing it. |
| 17 | **Subject: Expense report approved**<br><br>Hi Carlos,<br><br>Your March expense report for $684.20 has been approved. Reimbursement will be included in the April 15 payroll deposit. You do not need to take any further action.<br><br>Finance | Carlos’s $684.20 March expense report was approved, and reimbursement will arrive with the April 15 payroll deposit; no action is required. | good | It faithfully captures the approval, amount, payment timing, and lack of required action. |
| 18 | **Subject: Dental appointment reminder**<br><br>This is a reminder that your dental cleaning is scheduled for Tuesday, July 9 at 3:30 p.m. at our Oak Street clinic. Please arrive 10 minutes early and bring your insurance card. Call us at least 24 hours ahead if you need to reschedule. | The dental appointment is Wednesday, July 10 at 4:30 p.m. at the Pine Avenue clinic, and the patient should arrive 30 minutes early. | bad | It changes the date, time, location, and requested arrival time. |
| 19 | **Subject: Quarterly engagement survey**<br><br>Hi everyone,<br><br>The quarterly engagement survey is open through Friday, January 24. It takes about seven minutes, and responses are anonymous. Participation is optional, though we hope everyone will share feedback using the link below.<br><br>People Operations | The anonymous, optional engagement survey takes about seven minutes and is open through Friday, January 24. | good | It concisely preserves the deadline, anonymity, estimated time, and optional status. |
| 20 | **Subject: New data analyst joining**<br><br>Team,<br><br>Please welcome Sofia Nguyen, who joins us Monday as a data analyst on the Customer Insights team in Chicago. She previously worked at Northstar Retail and will report to Jamal Brooks.<br><br>Best,<br>Talent Team | Sofia Nguyen is starting today as a senior data scientist in New York and will lead the Customer Insights team. | bad | It changes the start date, title, location, and role by claiming she will lead the team. |
| 21 | **Subject: Q4 Marketing Campaign Update**<br><br>Hi team,<br><br>Social media engagement is up 25% month-over-month due to the new content calendar and paid ad experiments.<br><br>Newsletter open rate dropped from 42% to 35%; we'll test new subject lines next week.<br><br>The product video campaign is delayed until November, pending legal approval; creative assets are ready.<br><br>Please ensure all campaign tracking links are added by Friday.<br><br>Best,<br>Priya | Social media engagement rose 25% month-over-month, driven by the new content calendar and paid ad experiments. Newsletter open rate fell from 42% to 35%; new subject lines will be tested next week. Product video campaign is delayed to November pending legal approval; creative assets are ready. Tracking links are due Friday. | good | Real Version A output: all four items and every number kept in 51 words, nothing added. |
| 22 | **Subject: Q4 Marketing Campaign Update**<br><br>(same email as row 21) | Social media engagement climbed 25% month-over-month in Q4, driven by the new content calendar and paid ad experiments, giving the marketing team clear momentum. Creative assets for the product video campaign are also complete and ready to go. On the risk side, the newsletter open rate fell from 42% to 35%, and the team will begin testing new subject lines next week to reverse the decline. The product video campaign itself has slipped to November while it awaits legal approval, making that sign-off the key dependency. Priya has also asked that all campaign tracking links be added by Friday so performance can be measured accurately. | bad | Real Version B output: facts are correct, but it adds commentary that is not in the email ("clear momentum", "key dependency", "so performance can be measured accurately"). |

## Human curation

- Rows 1 to 20 are LLM-generated with first-pass labels. All 20 labels were reviewed and kept.
- Rows 21 and 22 are real outputs from the Module 1 Version A and Version B runs (generator: Claude), added and labelled by hand.
- Row 22 is the only row where the facts are right and the summary still fails, because of added commentary.

## Label distribution

| Label | Count | Share |
|---|---:|---:|
| `good` | 11 | 50% |
| `bad` | 11 | 50% |
| **Total** | **22** | **100%** |

## Evaluation rubric

Evaluate each candidate summary against the corresponding input email using the following criteria.

### 1. Faithfulness

- **Good:** Every claim is supported by the email; no dates, amounts, names, outcomes, or other facts are changed or invented.
- **Bad:** The summary contradicts the email, adds unsupported claims, or presents uncertainty or a conditional statement as fact.

### 2. Coverage of key information

- **Good:** It includes the email’s main purpose plus any essential action, owner, deadline, status, or consequence.
- **Bad:** It omits a detail that materially changes what the reader needs to know or do.

### 3. Concision

- **Good:** It is meaningfully shorter than the email and removes greetings, sign-offs, repetition, and secondary detail.
- **Bad:** It is excessively wordy, repeats most of the source, or adds commentary that does not help the reader.

### 4. Clarity

- **Good:** It is direct, easy to understand, and makes actors, actions, dates, and conditions unambiguous.
- **Bad:** It is vague, confusing, or written in a way that obscures the central message.

### 5. Actionability

- **Good:** When the email requires action, the summary states what must be done, by whom, and by when; when no action is needed, it does not invent one.
- **Bad:** It misses or changes a required action, deadline, or responsible party, or invents an action that the email does not request.

## First-pass labeling rule

Assign `good` only when the summary is faithful, adequately covers the key information, and is clear and concise. Assign `bad` when it contains any material factual error, misses an essential action or deadline, or is so verbose or vague that it fails as a useful summary.

