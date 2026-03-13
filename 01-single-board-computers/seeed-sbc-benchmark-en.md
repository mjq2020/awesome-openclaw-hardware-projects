# Seeed Studio SBC Benchmark for OpenClaw

**Version**: v1.0 | **Date**: 2026-03-13

---

## 1. Document Objective

Establish an OpenClaw performance evaluation standard for Seeed Studio single-board computers, helping users select the appropriate hardware platform.

---

## 2. Evaluation Goals

1. **Hardware Compatibility Assessment** — Determine the baseline capability of each SBC product to run OpenClaw
2. **Performance Tiering** — Establish a 1–5 star rating system for quick hardware selection
3. **Real-World Performance Validation** — Verify theoretical performance through actual scenario tests
4. **Cost-Effectiveness Analysis** — Evaluate value for money and provide recommendations for different budgets

**Target Use Cases**: Individual developers / Edge computing / Enterprise private deployment / Education & Research

---

## 3. Benchmark Architecture

This benchmark uses a **dual-dimension evaluation system: Static Scoring + Dynamic Testing**.

- **Static Scoring (Hardware Baseline)**: CPU / Memory / Storage / Composite Score, each rated 1–5 stars
- **Dynamic Testing (Real-World Performance)**: Installation & startup / LLM response / Tool calls / Concurrency / 24h stability / Network I/O

---

## 4. Static Scoring Criteria

> Static scoring only evaluates hardware support for the OpenClaw runtime environment (CPU multi-core performance, memory capacity, storage speed). Local AI inference capability is not considered.

### 4.1 CPU Rating (1–5 Stars)

- ⭐: Dual-core Cortex-A53 @ 1.2GHz (or equivalent)
- ⭐⭐: Quad-core Cortex-A55 @ 1.8GHz (or equivalent)
- ⭐⭐⭐: Quad-core Cortex-A72 @ 1.5GHz / Intel Celeron J4105 (or equivalent)
- ⭐⭐⭐⭐: Quad-core Cortex-A76 @ 2.4GHz / 6-core Cortex-A78 / Intel Celeron J4125 (or equivalent)
- ⭐⭐⭐⭐⭐: 8-core RK3588 / Jetson Orin NX or above

### 4.2 Memory Rating (1–5 Stars)

- ⭐: 2GB | ⭐⭐: 4GB | ⭐⭐⭐: 8GB | ⭐⭐⭐⭐: 16GB | ⭐⭐⭐⭐⭐: 32GB+
- LPDDR5/DDR5 vs same-capacity LPDDR4: +0.5 stars (higher bandwidth benefits concurrent tasks)

### 4.3 Storage Rating (1–5 Stars)

- ⭐: microSD / eMMC 5.0, read <100 MB/s
- ⭐⭐: eMMC 5.1, read 100–200 MB/s
- ⭐⭐⭐: SATA SSD / USB3 SSD, read 200–500 MB/s
- ⭐⭐⭐⭐: NVMe Gen3, read 1–3 GB/s
- ⭐⭐⭐⭐⭐: NVMe Gen4, read >3 GB/s
- Baseline: 128GB+; +0.5 stars for 256GB+; +1 star for 512GB+

### 4.4 Composite Score Formula

**Static Composite = CPU × 0.4 + Memory × 0.3 + Storage × 0.3**

Bonus/penalty factors (±0.5 stars, applied at discretion):
- Network: Dual Gigabit or above +0.25 stars
- Cooling: Active cooling (fan/liquid) +0.25 stars; no heatsink −0.25 stars
- Expandability: NVMe/PCIe expansion slot +0.25 stars

---

## 5. Dynamic Testing Criteria

### 5.1 Unified Test Environment

- **OS**: Latest version of the product's recommended OS (see "Recommended OS" column in Section 6)
- **OpenClaw**: Latest stable release (record version number)
- **Node.js**: v22.x LTS
- **LLM**: Claude Sonnet 4.5 (standard) / Claude Haiku (lightweight)
- **Network**: Wired Gigabit

### 5.2 Installation & Startup

Metrics: `npm install` duration / cold start / warm start / idle memory

- ⭐⭐⭐⭐⭐: Install <3 min, cold start <5s, warm start <2s
- ⭐⭐⭐⭐: Install 3–5 min, cold start 5–10s
- ⭐⭐⭐: Install 5–10 min, cold start 10–20s
- ⭐⭐: Install 10–15 min, cold start 20–30s
- ⭐: Install >15 min, cold start >30s

### 5.3 Basic Command Response (TTFT / TPS)

Test commands: Q&A / File read / Code generation / Complex reasoning / Multi-turn dialogue (3 runs each, take average)

- ⭐⭐⭐⭐⭐: TTFT <500ms, TPS >50
- ⭐⭐⭐⭐: TTFT 500ms–1s, TPS 30–50
- ⭐⭐⭐: TTFT 1–2s, TPS 20–30
- ⭐⭐: TTFT 2–3s, TPS 10–20
- ⭐: TTFT >3s, TPS <10

### 5.4 Tool Call Performance

Test items: File read/write / Shell command execution / Web search / Multi-tool chained calls

Metrics: Tool call latency / execution time / end-to-end completion time

### 5.5 Concurrent Tasks

Run 3 simultaneous OpenClaw sessions (long-text generation / code review / file+network operations)

- ⭐⭐⭐⭐⭐: 3 sessions smooth, response time increase <20%
- ⭐⭐⭐⭐: 20–50% increase
- ⭐⭐⭐: 50–100% increase
- ⭐⭐: 2 sessions usable, 3rd stutters
- ⭐: Only 1 session runs smoothly

### 5.6 24-Hour Stability

Execute standard commands every hour; record memory growth rate / response time standard deviation / crash count / system temperature

- ⭐⭐⭐⭐⭐: No crashes, memory growth <5%, variance <10%
- ⭐⭐⭐⭐: Memory growth 5–10%, variance 10–20%
- ⭐⭐⭐: Memory growth 10–20%, variance 20–30%
- ⭐⭐: Occasional reboots
- ⭐: Frequent crashes or OOM

### 5.7 Network I/O

Test items: Download 100 MB file / 10 concurrent API calls / 5000-character streaming response

---

## 6. Product List

Products grouped by platform. **Recommended OS** is sourced from official Seeed Studio Wiki documentation and platform vendor support.

### 6.1 Jetson Series (NVIDIA Platform)

| Model | CPU | Memory | Storage | Recommended OS | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|---|
| reComputer J4012 | Jetson Orin NX 6-core Cortex-A78AE | 16GB LPDDR5 | 128GB NVMe SSD | **JetPack 6.1** (Ubuntu 22.04) | GbE + WiFi/BT | ⭐⭐⭐⭐⭐ Flagship | — |
| reComputer J3010 | Jetson Orin Nano 6-core | 8GB LPDDR5 | 128GB NVMe SSD | **JetPack 6.1** (Ubuntu 22.04) | GbE + WiFi/BT | ⭐⭐⭐⭐ Highly Recommended | — |
| reComputer J2012 | Jetson Xavier NX 6-core Carmel | 16GB LPDDR4x | 128GB NVMe SSD | **JetPack 5.1.4** (Ubuntu 20.04) | GbE | ⭐⭐⭐⭐ Recommended | — |
| reComputer J2011 | Jetson Xavier NX 6-core Carmel | 8GB LPDDR4x | 128GB NVMe SSD | **JetPack 5.1.4** (Ubuntu 20.04) | GbE | ⭐⭐⭐⭐ Recommended | — |
| reComputer J1020 | Jetson Nano 4-core Cortex-A57 | 4GB LPDDR4 | 16GB eMMC | **JetPack 4.6.6** (Ubuntu 18.04) ⚠️ | GbE | ⭐⭐ Basic | — |
| reComputer J1010 | Jetson Nano 4-core Cortex-A57 | 4GB LPDDR4 | 16GB eMMC | **JetPack 4.6.6** (Ubuntu 18.04) ⚠️ | GbE | ⭐⭐ Basic | — |

> ⚠️ Jetson Nano (J1020/J1010) is a legacy platform. JetPack max support is 4.6.6 (Ubuntu 18.04). Node.js v22 requires manual compilation. Recommended for testing only.

### 6.2 Raspberry Pi Series (CM4/CM5/RPi5 Platform)

**6.2.1 Edge AI Computers (CM5 + Hailo-8)**

| Model | CPU | Memory | Storage | Recommended OS | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|---|
| reComputer AI Industrial R2235 | RPi CM5 4-core Cortex-A76 | 8/16GB | 32GB eMMC + NVMe | **RPi OS Bookworm** (Debian 12) | 4x GbE (PoE) | ⭐⭐⭐⭐⭐ Industrial Flagship | — |
| reComputer Industrial R2045 | RPi CM5 4-core Cortex-A76 | 8/16GB | 32GB eMMC + NVMe | **RPi OS Bookworm** (Debian 12) | GbE + PoE | ⭐⭐⭐⭐⭐ Industrial Flagship | — |
| reComputer Industrial R2135 | RPi CM5 4-core Cortex-A76 | 8/16GB | 32GB eMMC + NVMe | **RPi OS Bookworm** (Debian 12) | GbE + PoE | ⭐⭐⭐⭐⭐ Industrial Flagship | — |
| reComputer AI R2130 | RPi 5 4-core Cortex-A76 | 8/16GB | NVMe SSD | **RPi OS Bookworm** (Debian 12) | GbE | ⭐⭐⭐⭐⭐ Highly Recommended | — |
| reComputer AI Industrial R2135 | RPi CM5 4-core Cortex-A76 | 8/16GB + 32GB eMMC | NVMe SSD | **RPi OS Bookworm** (Debian 12) | GbE | ⭐⭐⭐⭐⭐ Highly Recommended | — |

**6.2.2 Edge Controllers (Industrial IoT)**

| Model | CPU | Memory | Storage | Recommended OS | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|---|
| reComputer Industrial R2035 | RPi CM5 4-core Cortex-A76 | 8/16GB | 32GB eMMC + NVMe | **RPi OS Bookworm** (Debian 12) | GbE + PoE | ⭐⭐⭐⭐ Industrial | — |
| reComputer Industrial R2135-10 | RPi CM5 4-core Cortex-A76 | 8/16GB | 32GB eMMC + NVMe | **RPi OS Bookworm** (Debian 12) | GbE + PoE | ⭐⭐⭐⭐ Industrial | — |
| reComputer R1000 | RPi CM4 4-core Cortex-A72 | 2/4/8GB | 8/16/32GB eMMC | **RPi OS Bookworm** (Debian 12) | 2x GbE | ⭐⭐⭐ Recommended | — |
| reComputer R1100 | RPi CM4 4-core Cortex-A72 | 2/4/8GB | 8/16/32GB eMMC | **RPi OS Bookworm** (Debian 12) | 2x GbE | ⭐⭐⭐ Recommended | — |
| EdgeBox RPi 200 | RPi CM4 4-core Cortex-A72 | 1/2/4/8GB | 8/16/32GB eMMC | **RPi OS Bookworm** (Debian 12) | GbE | ⭐⭐⭐ Recommended | — |

**6.2.3 HMI Devices**

| Model | CPU | Memory | Storage | Recommended OS | Display | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|---|---|
| reTerminal | RPi CM4 4-core Cortex-A72 | 4/8GB LPDDR4 | 32GB eMMC | **RPi OS Bookworm** (Debian 12) | 5" 1280×720 touch | GbE + WiFi/BT | ⭐⭐⭐ Recommended | — |
| reTerminal DM | RPi CM4 4-core Cortex-A72 | 4/8GB LPDDR4 | 32GB eMMC | **RPi OS Bookworm** (Debian 12) | 10.1" IP65 industrial touch | GbE + WiFi/BT | ⭐⭐⭐ Recommended | — |
| reRouter CM4 | RPi CM4 4-core Cortex-A72 | 4GB LPDDR4 | 32GB eMMC | **RPi OS Bookworm** (Debian 12) | None | 2x GbE + WiFi/BT | ⭐⭐⭐ Recommended | — |

### 6.3 x86 Series (Intel Platform)

| Model | CPU | Memory | Storage | Recommended OS | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|---|
| ODYSSEY X86 J4125 v2 | Intel Celeron J4125 4-core 2.0–2.7GHz + RP2040 | 8GB LPDDR4 | 64GB eMMC | **Ubuntu 22.04 LTS** (also supports Win11) | 2x 2.5GbE + WiFi/BT | ⭐⭐⭐⭐ x86 Pick | — |
| ODYSSEY X86 J4105 | Intel Celeron J4105 4-core 1.5–2.5GHz + ATSAMD21 | 8GB LPDDR4 | 64GB eMMC | **Ubuntu 22.04 LTS** (standard x86) | GbE + WiFi/BT | ⭐⭐⭐ Usable | — |

### 6.4 General-Purpose SBCs (Standard Development Boards)

> Mainstream general-purpose single-board computers commonly deployed in the OpenClaw community, suitable for individual developers and educational use.

**6.4.1 Official Raspberry Pi Series**

> 💡 RPi 5 / 4B support both SD card and NVMe storage options — performance differs significantly, listed separately:

| Model | Storage Option | Memory | Recommended OS | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|
| Raspberry Pi 5 (8GB) + NVMe HAT | NVMe SSD (via M.2 HAT+, >800 MB/s) | 8GB LPDDR4X | **RPi OS Bookworm** / Ubuntu 24.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐⭐⭐⭐ Highly Recommended | — |
| Raspberry Pi 5 (8GB) + SD Card | microSD (UHS-I, ~45 MB/s) | 8GB LPDDR4X | **RPi OS Bookworm** / Ubuntu 24.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐⭐⭐ Recommended | — |
| Raspberry Pi 5 (4GB) + NVMe HAT | NVMe SSD (via M.2 HAT+, >800 MB/s) | 4GB LPDDR4X | **RPi OS Bookworm** / Ubuntu 24.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐⭐⭐ Recommended | — |
| Raspberry Pi 5 (4GB) + SD Card | microSD (UHS-I, ~45 MB/s) | 4GB LPDDR4X | **RPi OS Bookworm** / Ubuntu 24.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐⭐ Usable | — |
| Raspberry Pi 4B (8GB) + USB3 SSD | USB3 external SSD (~400 MB/s) | 8GB LPDDR4 | **RPi OS Bookworm** / Ubuntu 22.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐⭐⭐ Recommended | — |
| Raspberry Pi 4B (8GB) + SD Card | microSD (UHS-I, ~45 MB/s) | 8GB LPDDR4 | **RPi OS Bookworm** / Ubuntu 22.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐⭐ Usable | — |
| Raspberry Pi 4B (4GB) + SD Card | microSD (UHS-I, ~45 MB/s) | 4GB LPDDR4 | **RPi OS Bookworm** / Ubuntu 22.04 | GbE + WiFi 5 / BT 5.0 | ⭐⭐ Marginal | — |
| Raspberry Pi 4B (2GB) + SD Card | microSD (UHS-I, ~45 MB/s) | 2GB LPDDR4 | **RPi OS Bookworm** / Ubuntu 22.04 | GbE + WiFi 5 / BT 5.0 | ⭐ Not Recommended | — |

**6.4.2 RockChip RK3588 Series (High-Performance General SBCs)**

| Model | CPU | Memory | Storage | Recommended OS | Network | OpenClaw Static Rating | Dynamic Result |
|---|---|---|---|---|---|---|---|
| Radxa ROCK 5B+ | RK3588 4×A76+4×A55 @ 2.4GHz | 4/8/16/32GB LPDDR5 | eMMC + NVMe Gen3 M.2 | **Armbian** / Ubuntu 22.04 (community) | 2.5GbE + WiFi 6 | ⭐⭐⭐⭐⭐ Performance Flagship | — |
| Orange Pi 5 Plus | RK3588 4×A76+4×A55 @ 2.4GHz | 4/8/16GB LPDDR4x | eMMC + 2x NVMe M.2 | **Orange Pi OS** (Ubuntu 22.04 base) | 2x 2.5GbE + WiFi 6E / BT 5.3 | ⭐⭐⭐⭐⭐ Performance Flagship | — |
| Orange Pi 5 Max | RK3588 4×A76+4×A55 @ 2.4GHz | 8/16GB LPDDR5 | eMMC + NVMe M.2 | **Orange Pi OS** (Ubuntu 22.04 base) | 2.5GbE + WiFi 6E / BT 5.3 | ⭐⭐⭐⭐⭐ Performance Flagship | — |
| Orange Pi 5 (4GB) | RK3588S 4×A76+4×A55 @ 2.0GHz | 4GB LPDDR4x | eMMC / microSD | **Orange Pi OS** (Ubuntu 22.04 base) | GbE | ⭐⭐⭐⭐ Recommended | — |

> ⚠️ RK3588: Ubuntu does not provide native support; community images required (Armbian or Orange Pi OS). Node.js v22 can be installed via fnm.

### 6.5 Quick Selection Guide

| Use Case | Recommended Product | Reason |
|---|---|---|
| High-performance server | reComputer J4012 / AI R2130 | Ample memory, strong CPU |
| Industrial edge deployment | reComputer R2235 / R2135 | Industrial-grade reliability, wide-temp operation |
| Personal/home OpenClaw | RPi 5 (8GB) + NVMe HAT | Best value, mature official OS |
| Performance-first general SBC | Radxa ROCK 5B+ / Orange Pi 5 Plus | Up to 32GB RAM, 2.5GbE |
| Lightweight gateway | reComputer R1100 / EdgeBox RPi 200 | Low power, stable and reliable |
| x86 compatibility required | ODYSSEY X86 J4125 v2 | Standard Linux/Windows compatible |
| HMI interactive device | reTerminal / reTerminal DM | Built-in touchscreen, plug-and-play |

---

## 7. Final Scores

**Final Score = Static × 0.4 + Dynamic Average × 0.6**

Dynamic Average = (Installation + Basic Commands + Tool Calls + Concurrency + Stability + Network I/O) / 6

| Model | Static Score | Dynamic Score | Final Score |
|---|---|---|---|
| reComputer J4012 | ⭐⭐⭐⭐⭐ Flagship | — | — |
| reComputer J3010 | ⭐⭐⭐⭐ Highly Recommended | — | — |
| reComputer J2012 | ⭐⭐⭐⭐ Recommended | — | — |
| reComputer J2011 | ⭐⭐⭐⭐ Recommended | — | — |
| reComputer J1020 | ⭐⭐ Basic | — | — |
| reComputer J1010 | ⭐⭐ Basic | — | — |
| reComputer AI Industrial R2235 | ⭐⭐⭐⭐⭐ Industrial Flagship | — | — |
| reComputer Industrial R2045 | ⭐⭐⭐⭐⭐ Industrial Flagship | — | — |
| reComputer Industrial R2135 | ⭐⭐⭐⭐⭐ Industrial Flagship | — | — |
| reComputer AI R2130 | ⭐⭐⭐⭐⭐ Highly Recommended | — | — |
| reComputer AI Industrial R2135 | ⭐⭐⭐⭐⭐ Highly Recommended | — | — |
| reComputer Industrial R2035 | ⭐⭐⭐⭐ Industrial | — | — |
| reComputer Industrial R2135-10 | ⭐⭐⭐⭐ Industrial | — | — |
| reComputer R1000 | ⭐⭐⭐ Recommended | — | — |
| reComputer R1100 | ⭐⭐⭐ Recommended | — | — |
| EdgeBox RPi 200 | ⭐⭐⭐ Recommended | — | — |
| reTerminal | ⭐⭐⭐ Recommended | — | — |
| reTerminal DM | ⭐⭐⭐ Recommended | — | — |
| reRouter CM4 | ⭐⭐⭐ Recommended | — | — |
| ODYSSEY X86 J4125 v2 | ⭐⭐⭐⭐ x86 Pick | — | — |
| ODYSSEY X86 J4105 | ⭐⭐⭐ Usable | — | — |
| RPi 5 (8GB) + NVMe HAT | ⭐⭐⭐⭐⭐ Highly Recommended | — | — |
| RPi 5 (8GB) + SD Card | ⭐⭐⭐⭐ Recommended | — | — |
| RPi 5 (4GB) + NVMe HAT | ⭐⭐⭐⭐ Recommended | — | — |
| RPi 5 (4GB) + SD Card | ⭐⭐⭐ Usable | — | — |
| RPi 4B (8GB) + USB3 SSD | ⭐⭐⭐⭐ Recommended | — | — |
| RPi 4B (8GB) + SD Card | ⭐⭐⭐ Usable | — | — |
| RPi 4B (4GB) + SD Card | ⭐⭐ Marginal | — | — |
| RPi 4B (2GB) + SD Card | ⭐ Not Recommended | — | — |
| Radxa ROCK 5B+ | ⭐⭐⭐⭐⭐ Performance Flagship | — | — |
| Orange Pi 5 Plus | ⭐⭐⭐⭐⭐ Performance Flagship | — | — |
| Orange Pi 5 Max | ⭐⭐⭐⭐⭐ Performance Flagship | — | — |
| Orange Pi 5 (4GB) | ⭐⭐⭐⭐ Recommended | — | — |

### 7.1 Selection Recommendations

- 1–2 stars: Learning/testing only, not suitable for production
- 3 stars: Personal daily use, small projects
- 4 stars: Professional development, production deployment
- 5 stars: Enterprise-grade, high-concurrency, mission-critical workloads

---

## Appendix

**Glossary**: SBC (Single-Board Computer) / TTFT (Time To First Token) / TPS (Tokens Per Second) / NPU (Neural Processing Unit)

**References**: OpenClaw Docs https://docs.openclaw.ai | Seeed Wiki https://wiki.seeedstudio.com 

