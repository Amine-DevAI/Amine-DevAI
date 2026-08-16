<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=4FACFE&center=true&vCenter=true&width=700&lines=Systems+%26+Backend+Engineer;Go+%2B+C%2B%2B+%E2%80%94+Hardware+to+Distributed+Systems;I+build%2C+measure%2C+and+prove+it+with+real+numbers." alt="Typing SVG" />

</div>

<div align="center">

[![profile views](https://komarev.com/ghpvc/?username=Amine-DevAI&color=blueviolet&style=flat-square)](https://github.com/Amine-DevAI)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295)

</div>

---

### 👋 Mohamed Amine Mammar El Hadj

Engineer who works across the stack — from raw sockets and serial protocols up to backend services and distributed systems architecture. What ties it together isn't one language or one layer: it's an approach — build the correct version first, measure it under real conditions, and prove any claim with data instead of assumptions. That approach has shipped a real industrial system end-to-end, reverse-engineered undocumented hardware protocols, and benchmarked backend architecture decisions with load-tested numbers.

I fit wherever the problem is: hardware-adjacent systems work, backend services, infrastructure, or the parts in between that most people avoid because they require understanding more than one layer at once.

- 🎓 **B.S. in Computer Science** (Computer Systems) — University of Blida 1, top of class
- 🎓 Currently pursuing an **M.S. in Artificial Intelligence** (Engineering of Smart Systems)
- 🏭 Designed and built an **industrial pharmaceutical waste-tracking system** for a multinational pharma manufacturer's local plant — ALCOA+ compliant, end to end, solo
- ⚙️ Design, build, and benchmark **Go backend services** — queues, async workers, load testing, distributed-systems tradeoffs
- 🔧 Independent work in hardware protocol reverse-engineering — [details below](#-independent-work--ble-protocol-reverse-engineering)

---

### 🛠️ Tech Stack

<div align="center">
<img src="https://skillicons.dev/icons?i=cpp,go,python,dart,flutter,postgres,redis,docker,linux,cmake,git" />
</div>

<div align="center">

| Area | Tools |
|---|---|
| **Languages** | Go, C++ (17/20), Python, Dart, SQL |
| **Backend & Distributed Systems** | Go (`net/http` stdlib), REST APIs, WebSockets, Redis (queues/pub-sub), ClickHouse, PostgreSQL, load testing & benchmarking |
| **Systems & Low-Level** | Socket programming, serial I/O (RS232/USB), BLE/GATT, FFI, protocol reverse-engineering |
| **Infra & Tooling** | Docker, Git, CMake, Linux |
| **Cross-platform** | Windows (Win32 overlapped I/O) · Linux (termios, BlueZ/D-Bus) · Flutter desktop |
| **Practice** | Documentation-driven development, modular architecture, audit-first data design, measure-then-optimize |

</div>

---

### ⚙️ Backend & Distributed Systems — Go

Same approach as everything below, pointed at backend architecture: build the naive version correctly, measure it under real load, fix it, and prove the fix with numbers instead of a diagram.

| Repo | What it does |
|---|---|
| 📊 [`sync-vs-async-booking-engine`](https://github.com/Amine-DevAI/sync-vs-async-booking-engine) | A booking API built 3 ways — sync baseline → blocking side-effects → Redis-queued async — benchmarked with a custom C++ load tester against real running code. **9x throughput recovery**, p99 latency cut 66%, and a real production bug (100% failure rate in the naive version) traced to its root cause instead of hand-waved away. |

---

### 🏗️ Featured System — Industrial Pharmaceutical Waste Tracking

One connected system, built solo, from the scale on the factory floor to the screen a technician taps:

```
Scale (RS232/USB) → C++ acquisition bridge → C++ backend engine (FFI) → Flutter desktop client
```

| Repo | What it does |
|---|---|
| 🎓 [`Graduation-Internship`](https://github.com/Amine-DevAI/Graduation-Internship) | The thesis + defense behind the whole project — ALCOA+ compliant pharma waste digitalization |
| ⚖️ [`industrial-scale-data-acquisition-bridge`](https://github.com/Amine-DevAI/industrial-scale-data-acquisition-bridge) | Cross-platform C++ library reading industrial scales, hand-rolled serial I/O for Windows *and* Linux |
| 🧠 [`ffi-signal-core`](https://github.com/Amine-DevAI/ffi-signal-core) | The native C++ engine — auth, RBAC, audit trail, 5 concurrent WebSockets, opaque-handle FFI |
| 📱 [`waste-tracking-flutter-client`](https://github.com/Amine-DevAI/waste-tracking-flutter-client) | The Flutter desktop client — 13 FFI binding modules, zero REST layer, direct native interop |
| 🖥️ [`industrial-backend-gateway`](https://github.com/Amine-DevAI/industrial-backend-gateway) | Sanitized, modular showcase of the C++20 backend gateway — API routing + OpenSSL crypto |

---

### 🩺 Independent Work — BLE Protocol Reverse Engineering

**[`bw-ba1-ble-gatt-reverse-engineering`](https://github.com/Amine-DevAI/bw-ba1-ble-gatt-reverse-engineering)** — a fully reverse-engineered BLE GATT protocol and C++/BlueZ driver for a blood pressure monitor after its vendor discontinued the companion app and left the hardware undocumented.

With no SDK and no vendor support available, I enumerated the device's GATT services directly, correlated raw notification traffic with physical device behavior, and reconstructed the protocol from scratch: the write sequence that triggers a measurement, the packet format for live cuff pressure during inflation, and the 14-byte frame encoding the final systolic/diastolic/pulse/arrhythmia result. I implemented the driver against BlueZ's D-Bus API with no third-party BLE wrapper, then ported the same protocol logic into a Flutter application.

This is a general skill I've applied more than once — see also the serial protocol reverse-engineering in `industrial-scale-data-acquisition-bridge` above. Undocumented byte offsets in the result packet are explicitly marked unknown rather than guessed.

---

### 📈 Activity

<div align="center">
<img src="https://streak-stats.demolab.com?user=Amine-DevAI&theme=dark&hide_border=true&background=00000000" height="165"/>
</div>

<div align="center">
<img src="https://github-readme-activity-graph.vercel.app/graph?username=Amine-DevAI&theme=react-dark&hide_border=true&bg_color=00000000" width="100%"/>
</div>

---

<div align="center">

**Open to opportunities in backend, systems, and infrastructure engineering — freelance or full-time.**
Reach out — [LinkedIn](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295) · open an issue on any repo above

</div>
