# Cache It Right: HTTP Caching Headers That Save Your Server

Every time a browser re-downloads a file it already has, you pay for bandwidth, latency, and server load. HTTP caching headers let you tell the browser exactly how long it can reuse a response — and when it must revalidate. For static assets with a content hash in the filename, use a long `max-age` with `immutable`; for HTML or API responses, prefer `no-cache` so the browser revalidates with ETag or Last-Modified instead of blindly trusting a stale copy.

```http
Cache-Control: public, max-age=31536000, immutable
```

For HTML entry points, pair revalidation with an ETag:

```http
Cache-Control: no-cache
ETag: "abc123"
```

A common mistake is caching HTML aggressively — one deploy and users keep seeing the old page because the browser never asked. The rule of thumb: immutable assets get a year, HTML gets revalidation, API responses get short TTLs or none.

**Why it matters:** Good caching cuts repeat load times dramatically and takes real load off your server — free performance, no new infrastructure.

#Backend #WebPerformance #HTTPCaching #WebDev #APIs
