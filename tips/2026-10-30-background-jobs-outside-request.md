# Move Slow Work Out of the Request: Use Background Jobs

If a request sends emails, generates a PDF, resizes images, or calls a slow third-party API, doing that work inline makes the user wait — and risks timeouts, duplicate submissions, and lost work when the connection drops. Instead, persist the job in a queue (or a jobs table) inside the request, return a fast response with a job id and status, and let a worker process it asynchronously. Workers can retry failures with backoff, and the client can poll a status endpoint or receive a webhook when the job finishes. Keep the request handler thin: validate input, enqueue, respond. Keep the worker idempotent, so a retry never sends the same email twice.

```js
// Request handler: validate, enqueue, respond fast
app.post("/reports", async (req, res) => {
  const job = await queue.add("generate-report", { userId: req.user.id });
  res.status(202).json({ jobId: job.id, status: "queued" });
});

// Worker: does the slow work, retries on failure
queue.process("generate-report", async (job) => {
  await generatePdf(job.data.userId); // idempotent: same input, same output
});
```

**Why it matters:** Fast responses, fewer timeouts, and retries that don't duplicate side effects — reliability your users can feel.

#Backend #NodeJS #WebDevelopment #SoftwareEngineering
