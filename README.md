<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=4FACFE&center=true&vCenter=true&width=600&lines=Systems+%26+Backend+Developer;M.S.+AI+Student+%E2%80%94+Engineering+of+Smart+Systems;I+build+software+from+the+metal+up." alt="Typing SVG" />

</div>

<div align="center">

[![profile views](https://komarev.com/ghpvc/?username=Amine-DevAI&color=blueviolet&style=flat-square)](https://github.com/Amine-DevAI)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295)

</div>

---

### 👋 Mohamed Amine Mammar El Hadj

I got here the way most systems people do: by taking things apart until I understood them. A dead scale protocol, an orphaned medical device, a monolith that needed to become something reviewable — same instinct every time. Read the bytes. Find the pattern. Build the clean version.

- 🎓 **B.S. in Computer Science** (Computer Systems) — University of Blida 1
- 🎓 Currently pursuing an **M.S. in Artificial Intelligence** (Engineering of Smart Systems)
- 🏭 Built and shipped an **industrial pharmaceutical waste-tracking system** for **Pfizer USP Alger**, ALCOA+ compliant, end to end — solo
- 🔧 Off the clock, I reverse-engineer hardware protocols that companies have abandoned — [see below](#-the-project-im-proudest-of)

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

### 🏗️ Featured System — Industrial Waste Tracking (Pfizer USP Alger)

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

### 🩺 The project I'm proudest of

In April, my dad's blood pressure monitor stopped working — not the hardware, the app. The vendor discontinued it, pulled it from the stores, and without it the device was just an expensive brick.

I told him to give it to me first.

No SDK, no docs, no vendor support — just a device speaking Bluetooth Low Energy to nobody. I opened a BLE scanner, read and wrote raw bytes until patterns emerged, and reconstructed the entire protocol: how to trigger a measurement, how the cuff streams live pressure, how the final reading is packed into 14 bytes. Then I ported it into a small Flutter app so he could use it like any other health app.

**[→ `bw-ba1-ble-gatt-reverse-engineering`](https://github.com/Amine-DevAI/bw-ba1-ble-gatt-reverse-engineering)**

*If you've got a medical or health device orphaned by a dead app, I mean it when I say — open an issue. I'll help if I can.*

---

### 📊 GitHub Stats

<div align="center">
<img src="https://github-readme-stats.vercel.app/api?username=Amine-DevAI&show_icons=true&theme=dark&hide_border=true&count_private=true" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Amine-DevAI&layout=compact&theme=dark&hide_border=true" height="165"/>
</div>

---

<div align="center">

**Open to opportunities in systems, backend, and embedded software.**
Reach out — [LinkedIn](https://www.linkedin.com/in/mohamed-amine-mammar-el-hadj-715a41295) · open an issue on any repo above

</div>
