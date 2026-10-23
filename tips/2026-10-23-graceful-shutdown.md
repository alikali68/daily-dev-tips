# Graceful Shutdowns: Let Your Server Finish Its Work Before It Dies

Deployments kill your process — and if you don't handle SIGTERM, in-flight requests die mid-write. The pro fix is a graceful shutdown: on SIGTERM, stop accepting new connections, let active ones finish, then close the database pool and exit. In Node.js:

```js
process.on('SIGTERM', () => {
  server.close(() => {          // stops accepting new connections
    dbPool.end();               // drain in-flight queries, then close
    process.exit(0);
  });
  setTimeout(() => process.exit(1), 10_000).unref(); // hard deadline
});
```

Note `server.close()` only fires its callback once all keep-alive connections end — the timeout is your insurance against a hung client. Kubernetes sends SIGTERM 30s before SIGKILL by default, so your handler's budget is the `terminationGracePeriodSeconds` minus headroom.

**Why it matters:** Dropped connections during deploys corrupt payments, duplicate webhooks, and erode user trust — a 15-line handler turns every deploy from a gamble into a non-event.

#Backend #NodeJS #DevOps #WebDevelopment
