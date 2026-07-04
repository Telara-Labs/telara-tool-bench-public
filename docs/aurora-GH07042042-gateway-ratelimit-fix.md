# Aurora gateway rate-limiter fix (GH07042042)

BEFORE: config/gateway.yaml rate_limiter.burst = 5
AFTER:  config/gateway.yaml rate_limiter.burst = 500

Root cause: undersized burst rejects legitimate retry bursts under load, surfacing as intermittent HTTP 500s at checkout. Tracking: #216 (symptom), #215 (investigation).
