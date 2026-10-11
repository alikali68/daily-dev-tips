# Reuse Database Connections With a Pool

Opening a new database connection on every request is one of the most expensive things a backend can do. Each handshake costs milliseconds of latency and memory, and under traffic spikes it can exhaust your database's connection limit entirely — taking down your whole API.

A connection pool solves this by keeping a fixed set of open connections and lending them to requests as needed, returning them to the pool when done:

```python
from psycopg2 import pool

db_pool = pool.SimpleConnectionPool(
    minconn=2, maxconn=10,
    dbname="shop", user="app", password="***"
)

def get_products():
    conn = db_pool.getconn()
    try:
        with conn.cursor() as cur:
            cur.execute("SELECT id, name, price FROM products")
            return cur.fetchall()
    finally:
        db_pool.putconn(conn)
```

Size the pool deliberately: `maxconn` should match your database's capacity divided by the number of app instances, and always set a timeout so slow queries can't hold connections forever. Monitor pool wait time — a growing queue of waiting requests is your earliest signal to scale.

**Why it matters:** Connection pooling turns database access from a per-request cost into a shared resource, keeping your API fast and your database alive under traffic spikes.

#backend #webdev #performance #databases #coding
