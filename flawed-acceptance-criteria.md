# Flawed Acceptance Criteria: Block 2, Pair AC, Step 1

These three acceptance criteria were drafted in a previous session on the Meridian
engagement. Each one has a factual error: it does not match what the stakeholders actually
said in the source material. Your job is to find the errors, with AI, by checking every
criterion against the source material. Follow step 1 in `block2-own-prompts.md`.

---

## AC-014: Resolution timeframe

**Story:** As a complaints handler, I want the system to flag a complaint as overdue if it
has not been resolved within the target time, so that I can prioritise my work.

**Acceptance criteria (as drafted):**
```
Given a complaint has been open for more than 5 working days
When a handler views the complaint
Then the system displays an "overdue" warning
And the complaint automatically escalates to the team leader
```

---

## AC-027: Customer non-response

**Story:** As a complaints handler, I want complaints to close automatically if the customer
stops responding, so that I don't have to chase unresponsive customers indefinitely.

**Acceptance criteria (as drafted):**
```
Given a customer has not responded to an information request for 7 days
When the 7-day period elapses
Then the complaint status changes to "closed"
And the customer receives a closure notification
```

---

## AC-041: Business customer complaints

**Story:** As a business customer, I want to submit complaints through the same system as
residential customers, so that my complaint is tracked consistently.

**Acceptance criteria (as drafted):**
```
Given a business customer submits a complaint
When the complaint is received
Then it follows the standard residential complaint workflow
And is assigned to a complaints handler in the standard queue
```
