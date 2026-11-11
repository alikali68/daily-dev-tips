# Rate Limiting: Protect Your API Before Traffic Does

Every public API eventually meets a client that sends too many requests — a runaway loop, a scraper, or a genuine traffic spike. Without a limit, one bad actor can starve your database, inflate your hosting bill, or take the whole service down. Rate limiting caps how many requests a client (by IP, API key, or user) can make in a time window, and returns HTTP 429 when the cap is hit. Put the limiter early in your request pipeline, before expensive work like database queries, so rejected requests stay cheap. Use a sliding window or token bucket rather than a fixed window to avoid the burst-at-the-boundary problem, and always send `Retry-After` and `X-RateLimit-Remaining` headers so honest clients can back off gracefully. For distributed setups, store counters in Redis, not in process memory, or each server instance will enforce its own separate limit.

```js
// Express + express-rate-limit: 100 requests per 15 minutes per IP
import rateLimit from "express-rate-limit";

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  limit: 100,
  standardHeaders: "draft-7",
  legacyHeaders: false,
  message: { error: "Too many requests, please try again later." },
});

app.use("/api/", limiter);
```

**Why it matters:** A rate limiter is the cheapest insurance your API can buy — it turns a potential outage into a polite 429.

#Backend #API #RateLimiting #WebDev #NodeJS
