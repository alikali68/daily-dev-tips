# Retries Need Backoff and Jitter — Not Just a Loop

Retrying a failed request immediately is the fastest way to turn a small outage into a full one: every client hammering the same failing endpoint at the same moment creates a retry storm. Instead, wait longer between attempts with exponential backoff — 1s, 2s, 4s, 8s — and add random jitter so clients don't all retry in lockstep. Cap the total attempts (3–5 is usually enough) and only retry errors that are actually transient, like 429s, 503s, and network timeouts; retrying a 400 or a validation error just burns resources. If the service is down for a while, a circuit breaker that pauses retries entirely will save both sides.

```js
async function fetchWithRetry(url, attempts = 4) {
  for (let i = 0; i < attempts; i++) {
    try {
      const res = await fetch(url);
      if (res.ok) return res;
      if (res.status < 500 && res.status !== 429) throw new Error(`HTTP ${res.status}`);
    } catch (err) {
      if (i === attempts - 1) throw err;
    }
    const delay = Math.min(1000 * 2 ** i, 8000) + Math.random() * 500;
    await new Promise(r => setTimeout(r, delay));
  }
}
```

**Why it matters:** Backoff with jitter turns a retry from a second outage into a graceful recovery — your users wait a little longer, but the service gets a real chance to come back.

#Backend #APIs #WebDev #Reliability #Programming
