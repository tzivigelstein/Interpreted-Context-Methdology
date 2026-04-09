# Flow Tracing Method

How to trace a border's full flow without missing the parts where bugs hide.

## Why End-to-End

Bugs at borders rarely live in a single function. They live in the gaps between functions, between files, between processes. If you read one file at a time, the bug stays invisible because each file is internally consistent.

A trace follows the flow across every boundary it crosses, so you can see the assumptions on each side of each boundary.

## The 5 Questions

For every border, answer all five before moving on.

### 1. What triggers this flow?

- A user action (clicking a button, submitting a form)?
- A scheduled job (cron, Celery beat)?
- A webhook from an external service?
- A message from a queue?
- Another internal flow?

Capture the entry point with file:line.

### 2. What data does it read?

- From which database tables, with what filters?
- From which external APIs, with what query params?
- From which files, with what parsing assumptions?
- Are there limits on the read (LIMIT 500, pagination cap, time window)?

Capture the read sources with file:line.

### 3. What transformations does it apply?

- What does it add (default values, computed fields)?
- What does it remove (filtering, deduplication)?
- What does it assume about the input shape?
- Where are the parsing or validation steps?

Capture the transformation chain with file:line.

### 4. What does it write?

- To which database tables, with what mode (insert, update, upsert, delete)?
- To which external systems, with what payload?
- To which files or queues?
- What gets overwritten vs preserved?

Capture the write targets with file:line.

### 5. What does it report?

- Does the success/failure signal reflect the actual result, or only one step's result?
- Where does the error go if a step fails partway through?
- Is there a transaction boundary, or can the flow leave the system in a partial state?

Capture the reporting and error handling with file:line.

## Output Per Border

Write each trace as a section in `output/<repo>/<audit-slug>-traces.md`:

```
## [Border ID] - [Border name]

**Trigger:** [step 1 answer with file:line]
**Reads:** [step 2 answer with file:line]
**Transforms:** [step 3 answer with file:line]
**Writes:** [step 4 answer with file:line]
**Reports:** [step 5 answer with file:line]
```

Keep each trace focused. If a flow is too complex to fit on one page, you have probably found a complexity smell. Note it but trace what you can.
