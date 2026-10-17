# Idempotency Keys: Make Your API Retries Safe

Every payment or order endpoint eventually gets retried — by the client, a queue worker, or a flaky network resending the same request. Without protection, "exactly once" becomes "charged twice." Idempotency keys solve this: the client generates a unique key per logical operation (e.g. a UUID) and sends it in a header like `Idempotency-Key`. The server stores the key alongside the operation's result and, if the same key arrives again, returns the stored result instead of re-running the logic. Key it per operation — a fresh UUID for each "create order" intent, reused on retry — and expire keys after a sensible window (24–72h is common).

```js
// Express sketch (use Redis with a TTL in production)
const seen = new Map();
app.post("/orders", (req, res) => {
  const key = req.headers["idempotency-key"];
  if (seen.has(key)) return res.status(200).json(seen.get(key));
  const order = createOrder(req.body);
  seen.set(key, order);
  res.status(201).json(order);
});
```

**Why it matters:** Retries are inevitable in distributed systems; idempotency keys turn them from a double-charge risk into a harmless no-op — cheap insurance for any endpoint that moves money or mutates state.

#backend #api #nodejs #webdev #programming
