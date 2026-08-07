<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=4FACFE&center=true&vCenter=true&width=600&lines=Systems+%26+Backend+Developer;M.S.+AI+Student+%E2%80%94+Engineering+of+Smart+Systems;I+build+software+from+the+metal+up." alt="Typing SVG" />

</div>

<div align="center">

[![profile views](https://komarev.com/ghpvc/?username=Amine-DevAI&color=blueviolet&style=flat-square)](https://github.com/Amine-DevAI)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295)

</div>

---

### 👋 Mohamed Amine Mammar El Hadj

Systems and backend developer with a focus on low-level architecture, protocol-level work, and infrastructure that has to hold up under real constraints — hardware, compliance, and concurrency, not just a database and a REST endpoint.

- 🎓 **B.S. in Computer Science** (Computer Systems) — University of Blida 1
- 🎓 Currently pursuing an **M.S. in Artificial Intelligence** (Engineering of Smart Systems)
- 🏭 Designed and built an **industrial pharmaceutical waste-tracking system** for a multinational pharma manufacturer's local plant, ALCOA+ compliant, end to end, solo
- 🔍 All hardware protocol reverse-engineering in this portfolio — the industrial scale's serial protocol and a medical device's BLE protocol — was done independently, with no team and no supervision
- 🔧 Independent work in hardware protocol reverse-engineering — [details below](#-independent-work--ble-protocol-reverse-engineering)

---

### 🛠️ Tech Stack

<div align="center">
<img src="https://skillicons.dev/icons?i=cpp,python,dart,flutter,postgres,linux,cmake,git" />
</div>

<div align="center">

| Area | Tools |
|---|---|
| **Languages** | C++ (17/20), Python, Dart, SQL |
| **Systems & Low-Level** | Socket programming, serial I/O (RS232/USB), BLE/GATT, FFI, protocol reverse-engineering |
| **Backend** | PostgreSQL, REST APIs, WebSockets, OpenSSL, RBAC/auth design |
| **Cross-platform** | Windows (Win32 overlapped I/O) · Linux (termios, BlueZ/D-Bus) · Flutter desktop |
| **Practice** | Documentation-driven development, modular architecture, audit-first data design |

</div>

---

### 🏗️ Featured System — Industrial Pharmaceutical Waste Tracking

One connected system, built solo, from the scale on the factory floor to the screen a technician taps:

```
Scale (RS232/USB) → C++ acquisition bridge → C++ backend engine (FFI) → Flutter desktop client
```

| Repo | What it does |
|---|---|
| 🎓 [`Graduation-Internship`](https://github.com/Amine-DevAI/Graduation-Internship) | The thesis + defense behind the whole project — ALCOA+ compliant pharma waste digitalization |
| ⚖️ [`industrial-scale-data-acquisition-bridge`](https://github.com/Amine-DevAI/industrial-scale-data-acquisition-bridge) | Cross-platform C++ library reading industrial scales — serial protocol reverse-engineered solo from raw captures, hand-rolled I/O for Windows *and* Linux; the decoded protocol file is withheld as IP |
| 🧠 [`ffi-signal-core`](https://github.com/Amine-DevAI/ffi-signal-core) | The native C++ engine — auth, RBAC, audit trail, 5 concurrent WebSockets, opaque-handle FFI |
| 📱 [`waste-tracking-flutter-client`](https://github.com/Amine-DevAI/waste-tracking-flutter-client) | The Flutter desktop client — 13 FFI binding modules, zero REST layer, direct native interop |
| 🖥️ [`industrial-backend-gateway`](https://github.com/Amine-DevAI/industrial-backend-gateway) | Sanitized, modular showcase of the C++20 backend gateway — API routing + OpenSSL crypto |

---

### 🩺 Protocol Reverse Engineering — Case Study

**[`bw-ba1-ble-gatt-reverse-engineering`](https://github.com/Amine-DevAI/bw-ba1-ble-gatt-reverse-engineering)** — a fully reverse-engineered BLE GATT protocol and C++/BlueZ driver for a blood pressure monitor after its vendor discontinued the companion app and left the hardware undocumented.

With no SDK and no vendor support available, I enumerated the device's GATT services directly, correlated raw notification traffic with physical device behavior, and reconstructed the protocol from scratch: the write sequence that triggers a measurement, the packet format for live cuff pressure during inflation, and the 14-byte frame encoding the final systolic/diastolic/pulse/arrhythmia result. I implemented the driver against BlueZ's D-Bus API with no third-party BLE wrapper, then ported the same protocol logic into a Flutter application.

This is one of two protocols I've reverse-engineered from raw captures with no documentation available — the other being the industrial scale's serial protocol above. Undocumented byte offsets in the BLE result packet are explicitly marked unknown rather than guessed.

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

**Open to opportunities in systems, backend, and embedded software.**
Reach out — [LinkedIn](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295) · open an issue on any repo above

</div>
