<div align="center">

# Mohamed Amine Mammar El Hadj

### Backend Engineer — Go, distributed systems, performance under load

I build backend systems and then break them on purpose, with real load
tests, to prove what a design decision actually costs — not just to
describe it. Every project below ships with the numbers, the failure
modes, and the fix.

[![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)](https://go.dev)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white)](https://www.postgresql.org)
[![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)](https://redis.io)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)](https://kubernetes.io)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295)

</div>

---

## Why these projects exist

Most backend portfolios show working code. That proves you can follow a
tutorial. These three don't — each one exists to answer a specific
architectural question with a measured, reproducible answer:

- **What does a blocking side-effect actually cost you under load, in req/s and p99 ms — not in theory?**
- **How do you route data across independent shards without a full re-hash every time you add one?**
- **How do you build auth that revokes instantly, not just at expiry?**

Each repo below is self-contained, documented, and runnable in under five
minutes from a clean clone.

---

## Projects

<table>
<tr>
<td width="50%" valign="top">

### [Sync vs Async Booking Engine](https://github.com/Amine-DevAI/sync-vs-async-booking-engine)

Same API, built three times, load-tested against itself.

**9x** throughput recovered · **66%** p99 cut · found a **100%-failure
bug** the naive version was silently hiding

`Go` `PostgreSQL` `Redis` `ClickHouse` `C++ load tester`

</td>
<td width="50%" valign="top">

### [Consistent-Hash Sharding Proxy](https://github.com/Amine-DevAI/consistent-hashing-sharding-proxy)

Hand-rolled consistent hash ring routing across **5 independent Postgres
shards**, fully decoupled through Redis, deployed on Kubernetes.

`Go` `PostgreSQL x5` `Redis` `Kubernetes`

</td>
</tr>
<tr>
<td width="50%" valign="top">

### [JWT Auth Service](https://github.com/Amine-DevAI/implementation-golang-jwt-authentication)

Layered `Handler → Service → Repository` auth service with real
revocation — logout invalidates a token immediately, not at expiry.

`Go` `chi` `PostgreSQL` `JWT`

</td>
<td width="50%" valign="top">

### More on the way

Each new project targets one backend concept: gRPC microservices,
replication mechanics, rate limiting. Added here as they ship.

</td>
</tr>
</table>

---

## The numbers, side by side

| | Booking Engine — sync path | Booking Engine — async path | Sharding Proxy |
|---|---|---|---|
| Throughput | 193 req/s | 1,699 req/s | 5-shard routing, O(log n) lookup |
| p99 latency | 266ms | 92ms | 5s bounded worst case (timeout) |
| Success rate | **0%** (bug caught by the benchmark) | 100% | — |
| What broke it | Client blocked on 3 systems it didn't ask about | — | — |

---

## 1 · [Sync vs Async Booking Engine](https://github.com/Amine-DevAI/sync-vs-async-booking-engine)

**The question:** what does it cost to send email, SMS, and write an audit
log *inline*, before responding to the client — versus pushing that work
off the request path entirely?

**The build:** the same booking API, three times.

| | Phase 1 — Baseline | Phase 2 — Synchronous | Phase 3 — Async (Redis queue) |
|---|---|---|---|
| Avg throughput | 3,165 req/s | 193 req/s | 1,699 req/s |
| Avg p99 latency | 32ms | 266ms | 92ms |
| Success rate | 100% | **0%** | 100% |

**The finding that mattered more than the numbers:** phase 2's 0% success
rate wasn't a load-tester timeout — it was a real bug. The schema was
missing an `audit_logs` table, and the handler treated a failed audit
write (non-critical) as fatal to the whole request (critical). The booking
itself succeeded every time; the response lied about it. Async doesn't
just isolate this failure mode — it makes it structurally impossible,
since audit writes happen in a separate process against a separate
database on a path that can never touch the HTTP response.

**Built from scratch, not off the shelf:** the load generator itself —
multi-threaded C++17, raw sockets, lock-free per-thread metrics, warmup
exclusion, linear-interpolation percentiles — so every number above is
backed by code I can point to and explain, not a black-box tool.

`Go (net/http stdlib)` `PostgreSQL (TSRANGE + GIST exclusion constraints)` `Redis` `ClickHouse` `C++17` `Python (pandas/seaborn)`

---

## 2 · [Consistent-Hash Sharding Proxy](https://github.com/Amine-DevAI/consistent-hashing-sharding-proxy)

**The question:** how do you route keys across multiple databases without
a full re-shuffle every time a shard is added or removed?

**The build:** two services sharing zero code, connected only through
Redis. Server A takes HTTP requests and enqueues them; Server B — a pool
of goroutines — dequeues, resolves each key to a physical shard via a
hand-built consistent hash ring, executes against that shard's dedicated
Postgres connection, and writes the result back to a per-request response
key with a TTL.

**Why virtual nodes matter here:** each of the 5 shards is hashed into 3
positions on the ring, not one — smoothing load distribution so no single
shard becomes a hot spot. Ring lookups are O(log n) via binary search over
a sorted slice. Adding or removing a shard only moves the keys adjacent to
it on the ring — not every key in the system, which is the entire reason
consistent hashing exists over `hash(key) % N`.

**Deployment is real, not decorative:** full Kubernetes manifests for
Redis and 5 independent Postgres shard deployments, each pre-seeded via a
ConfigMap-driven init script — plus a Docker Compose path for a fast local
smoke test.

`Go` `PostgreSQL (5 shards)` `Redis (queue + response mailbox)` `Kubernetes` `crc32 hashing, no external library`

---

## 3 · [JWT Auth Service](https://github.com/Amine-DevAI/implementation-golang-jwt-authentication)

**The question:** how do you structure auth so each layer is testable in
isolation, and revocation actually revokes — not just waits out an expiry?

**The build:** strict `Handler → Service → Repository → DB` layering,
where every layer only knows the interface below it. The repository is the
only layer that knows Postgres exists; swapping the DB driver or router
never ripples upward.

**The detail that matters in production:** refresh tokens are validated by
an exact-match lookup against a `refresh_tokens_table`, not just signature
verification. That means logout or rotation invalidates a token
*immediately*, even if its signature is still technically valid until
expiry — a real gap in a lot of JWT implementations that only check the
signature.

**Documented honestly:** the README calls out its own known gaps —
including one real bug in the claims-parsing middleware (`&&` where it
should be `||`) — rather than presenting the code as finished. Adapted
from and credited to an upstream reference implementation for the layout
pattern; the licensing question that comes with that is addressed
explicitly in-repo rather than ignored.

`Go` `chi` `PostgreSQL (pgx)` `JWT (HS256)` `bcrypt`

---

## Adding a new project

1. Add it to the [Projects](#projects) grid and the summary table.
2. Add a `## N · [Name](link)` section below using this shape: **the
   question** it answers → **the build** → **the result** (numbers if you
   have them) → stack line.

No other structure to maintain.

---

<div align="center">

**B.S. Computer Science (Computer Systems), University of Blida 1 · currently pursuing an M.S. in AI**

[LinkedIn](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295) · [All repositories](https://github.com/Amine-DevAI?tab=repositories)

</div>
