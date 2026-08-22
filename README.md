<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=4FACFE&center=true&vCenter=true&width=700&lines=Systems+%26+Backend+Engineer;Go+%2B+C%2B%2B+%E2%80%94+Hardware+to+Distributed+Systems;I+build+it%2C+load+test+it%2C+then+fix+what+breaks." alt="Typing SVG" />

</div>

<div align="center">

[![profile views](https://komarev.com/ghpvc/?username=Amine-DevAI&color=blueviolet&style=flat-square)](https://github.com/Amine-DevAI)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295)

</div>

---

### About me

I'm Mohamed Amine Mammar El Hadj. I work across the stack, from serial
protocols and raw sockets up to backend services and distributed systems.
My usual process: build the straightforward version first, put real load
on it, and fix whatever the numbers actually show instead of what I
assumed would happen.

- B.S. Computer Science (Computer Systems), University of Blida 1, top 10% of class
- Currently doing an M.S. in AI (Engineering of Smart Systems)
- Built an industrial pharmaceutical waste-tracking system for a local pharma plant on my own, start to finish
- Lately working on Go backend services — queues, async workers, load testing

---

### Tech stack

<div align="center">
<img src="https://skillicons.dev/icons?i=cpp,go,python,dart,flutter,postgres,redis,docker,linux,cmake,git" />
</div>

<div align="center">

| Area | Tools |
|---|---|
| **Languages** | Go, C++ (17/20), Python, Dart, SQL |
| **Backend & distributed systems** | Go (`net/http` stdlib), REST APIs, WebSockets, Redis, ClickHouse, PostgreSQL, load testing |
| **Systems / low-level** | Socket programming, serial I/O (RS232/USB), BLE/GATT, FFI, protocol reverse-engineering |
| **Infra** | Docker, Git, CMake, Linux |
| **Cross-platform** | Windows (Win32 overlapped I/O), Linux (termios, BlueZ/D-Bus), Flutter desktop |

</div>

---

### Go backend work

Same habit as everything else here, pointed at backend architecture:
build the naive version, load test it, see what actually breaks, fix it,
and back the fix up with numbers instead of a diagram.

| Repo | What it is |
|---|---|
| [`sync-vs-async-booking-engine`](https://github.com/Amine-DevAI/sync-vs-async-booking-engine) | A booking API built three ways — sync baseline, blocking side-effects, Redis-queued async — benchmarked with a load tester I wrote in C++. Async recovered 9x the throughput the naive version lost, cut p99 latency by 66%, and the benchmark caught a real bug (0% success rate in the synchronous version) that a clean chart would've hidden. |
| [`consistent-hashing-sharding-proxy`](https://github.com/Amine-DevAI/consistent-hashing-sharding-proxy) | A key-value store sharded across 5 independent Postgres instances. Two services, no shared code, talking only through Redis. Routing is a consistent hash ring I wrote from scratch (virtual nodes, binary search lookup), deployed on Kubernetes with real shard manifests, not a toy setup. |
| [`implementation-golang-jwt-authentication`](https://github.com/Amine-DevAI/implementation-golang-jwt-authentication) | A layered auth service — handler, service, repository, each only aware of the layer below it through an interface. Refresh tokens are checked against a stored value on every use, so logging out actually revokes access immediately instead of waiting for the token to expire. |

---

### Featured system — industrial pharmaceutical waste tracking

One connected system, built solo, from the scale on the factory floor to
the screen a technician taps:

```
Scale (RS232/USB) → C++ acquisition bridge → C++ backend engine (FFI) → Flutter desktop client
```

| Repo | What it is |
|---|---|
| [`industrial-scale-data-acquisition-bridge`](https://github.com/Amine-DevAI/industrial-scale-data-acquisition-bridge) | Cross-platform C++ library for reading industrial scales, with serial I/O written by hand for both Windows and Linux |
| [`ffi-signal-core`](https://github.com/Amine-DevAI/ffi-signal-core) | The native C++ engine — auth, RBAC, audit trail, 5 concurrent WebSockets, opaque-handle FFI |
| [`waste-tracking-flutter-client`](https://github.com/Amine-DevAI/waste-tracking-flutter-client) | The Flutter desktop client — 13 FFI binding modules, no REST layer, talks directly to the native engine |
| [`industrial-backend-gateway`](https://github.com/Amine-DevAI/industrial-backend-gateway) | A sanitized, modular version of the C++20 backend gateway — API routing plus OpenSSL crypto |

---

### Side project — reverse-engineering a BLE protocol

**[`bw-ba1-ble-gatt-reverse-engineering`](https://github.com/Amine-DevAI/bw-ba1-ble-gatt-reverse-engineering)** — a blood pressure monitor whose vendor discontinued the companion app and never documented the hardware. I reverse-engineered the BLE GATT protocol and wrote a C++/BlueZ driver for it.

No SDK, no vendor support. I enumerated the device's GATT services
directly, watched the raw notification traffic against what the device
was physically doing, and pieced the protocol back together: the write
sequence that starts a measurement, the packet format for live cuff
pressure while it inflates, and the 14-byte frame that carries the final
systolic/diastolic/pulse/arrhythmia reading. The driver runs on BlueZ's
D-Bus API directly, no third-party BLE wrapper, and I later ported the
same protocol logic into a Flutter app.

I've done this kind of thing more than once — there's similar serial
protocol work in `industrial-scale-data-acquisition-bridge` above. Where
a byte in the result packet is still unknown, it's marked unknown rather
than guessed at.

---

### Activity

<div align="center">
<img src="https://streak-stats.demolab.com?user=Amine-DevAI&theme=dark&hide_border=true&background=00000000" height="165"/>
</div>

<div align="center">
<img src="https://github-readme-activity-graph.vercel.app/graph?username=Amine-DevAI&theme=react-dark&hide_border=true&bg_color=00000000" width="100%"/>
</div>

---

<div align="center">

Open to backend, systems, and infrastructure work — freelance or full-time.
[LinkedIn](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295) or open an issue on any repo above.

</div>
