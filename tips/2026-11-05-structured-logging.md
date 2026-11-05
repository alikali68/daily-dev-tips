# Structured Logging: Stop Grepping, Start Querying

Plain-text logs feel fine until 2 a.m., when you're grepping through thousands of lines trying to trace one failed request across three services. Structured logs fix this: every log line is a JSON object with consistent fields — timestamp, level, service, message, and a correlation ID that follows the request everywhere it goes.

```js
// One correlation ID per request, attached to every log line
app.use((req, res, next) => {
  req.id = req.headers["x-request-id"] ?? crypto.randomUUID();
  req.log = logger.child({ requestId: req.id, service: "checkout" });
  next();
});

req.log.info({ userId, amount }, "payment started");
```

Keep field names identical across services (`userId`, not `user_id` in one place and `user` in another), log at the right level (info for business events, error with stack traces, never debug in production), and never log secrets or full payloads. When every line is queryable, an incident becomes one filter — `requestId = "abc-123"` — instead of an hour of guessing.

**Why it matters:** structured logs turn debugging from archaeology into a database query — faster incidents, calmer on-call, happier users.

#Backend #DevTips #Logging #SoftwareEngineering
