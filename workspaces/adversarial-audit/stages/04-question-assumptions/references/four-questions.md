# The Four Questions

Four categories of broken assumptions. Apply each one to every traced flow. Each category has its own pattern of failure.

## Q1: "Are we the source of truth?"

The system writes data to an external system assuming it knows the complete or correct state. But the external system has its own state that the code does not model.

**How to find it:** For every WRITE operation to an external system, ask:

- What fields or state exist on the other side that we do not track?
- What happens to data we do NOT send? Does it get reset, preserved, or deleted?
- Could another actor (admin tool, manual edit, other integration) change the same data?

**Hypothesis pattern:** "When we write X to [external system], we send only fields A, B, C. Field D exists on the other side, and our write [resets it / leaves it stale / overwrites a manual change]."

## Q2: "Does input follow the expected format?"

The system assumes inputs (files, API responses, user data) follow a specific structure. Real-world inputs have variations the happy path does not cover.

**How to find it:** For every input the system processes, ask:

- What are the real-world variations, beyond the format spec?
- Look at actual user submissions: legacy data, third-party tools, manual edits.
- Is the format trusted from a label (extension, header, declared type), or verified from content?

**Hypothesis pattern:** "We assume [input X] has structure Y. Real-world inputs include [variation Z], which causes [parsing failure / silent miscategorization / data loss]."

## Q3: "Do operations happen in the expected order?"

The system assumes steps occur in a specific sequence. Users, concurrent processes, and partial failures can reorder them.

**How to find it:** For every multi-step flow, ask:

- What if step B happens before step A?
- What if step A succeeds but step B fails?
- What if a user does X before Y, even though the UI suggests Y first?
- What if the same flow runs twice concurrently?

**Hypothesis pattern:** "Step A is supposed to happen before step B. If [the order is reversed / B fails / they happen concurrently], the system [reports success but is in a partial state / loses data / gets stuck]."

## Q4: "Is our data complete?"

The system assumes it has all the relevant data. Queries have limits, external systems have entries the system does not know about, and data can be missing or stale.

**How to find it:** For every query feeding a critical operation, ask:

- What if this returns fewer results than reality?
- What exists in the external system that does not exist in our database?
- Is there a LIMIT, a pagination cap, or a time window that could silently truncate?
- Could the data be stale because of caching, eventual consistency, or a missed sync?

**Hypothesis pattern:** "We query [source] with [filter]. If the source has data we do not see (because of [LIMIT / sync gap / cache / pagination]), we [overwrite real data / silently delete / report wrong totals]."

## How to Apply

For each traced flow from stage 03, walk through Q1, Q2, Q3, Q4 in order. Each question generates zero or more hypotheses. A trace might generate hypotheses for all four questions, or only one or two.

Be paranoid here. A hypothesis is just a "what if". Validation in stage 05 will filter out the implausible ones. The cost of generating a wrong hypothesis is low. The cost of missing a real one is high.
