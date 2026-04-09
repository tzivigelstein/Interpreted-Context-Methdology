# Borders

A border is any point where the system trusts something it does not control. The audit looks for broken trust at every border.

## Definition

A border has two sides:

- **Inside**: code we wrote, state we manage, operations we sequence
- **Outside**: external systems, user-supplied data, concurrent processes, time

A border exists wherever inside-code reads or writes outside-state without a transaction that spans both sides.

## Border Checklist

When scanning a repo for borders, look for these. The list is not exhaustive. Flag anything that fits the definition above.

### Network Borders

- HTTP clients (requests, axios, fetch, httpx)
- API integrations (Stripe, Twilio, AWS SDKs, OAuth providers)
- Webhook receivers (incoming POST endpoints with external triggers)
- Webhook senders (outgoing POSTs to user-supplied URLs)
- gRPC, GraphQL, WebSocket clients

### Storage Borders

- Database writes (especially without transactions)
- Cache writes (Redis, Memcached, in-memory caches with TTL)
- Object storage (S3, GCS, blob stores)
- File system writes (especially shared volumes)
- Search index writes (Elasticsearch, Algolia)

### Input Borders

- File uploads from users
- Form submissions
- URL parameters and query strings
- Imported files (CSV, XML, JSON, ZIP archives)
- Command-line arguments
- Environment variables read at runtime

### Concurrency Borders

- Background jobs (Celery, Sidekiq, RQ, cron)
- Message queues (RabbitMQ, SQS, Kafka)
- Lock acquisition (database row locks, distributed locks)
- Async tasks that modify shared state
- Parallel HTTP requests that share results

### User Flow Borders

- Multi-step UIs (signup, checkout, onboarding)
- Resumable flows (the user can leave and come back)
- Admin tools that bypass normal flows
- Manual data corrections

### Time Borders

- Cron jobs and scheduled tasks
- TTL-based expiration
- Token issuance and validation
- Timestamps used for ordering

## Per-Border Capture Format

When stage 01 records a border, use this shape:

```
| ID | Border | Location | Direction | External System |
|----|--------|----------|-----------|-----------------|
| B01 | Mod push to ACSM | app/services/acsm_push.py:142 | out | ACSM API |
| B02 | Skin upload parsing | app/uploads/skin.py:67 | in | User uploads |
```

The ID is referenced in later stages. Direction is `in` (we read from outside), `out` (we write to outside), or `both`.
