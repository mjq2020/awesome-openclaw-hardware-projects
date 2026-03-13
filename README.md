# awesome-openclaw-hardware-projects

[![awesome](https://cdn.jsdelivr.net/gh/sindresorhus/awesome@main/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![License: CC0](https://img.shields.io/badge/License-CC0-lightgrey?style=flat&style=flat)](LICENSE)

> A community collection of OpenClaw hardware projects — enabling AI agents to interact with the physical world.

[OpenClaw](https://github.com/openclaw/openclaw) has transformed office automation and content creation, but its connection to the physical world remains underdeveloped. Unlike interacting with internet APIs, hardware integration lacks standardized interfaces and protocols. This field is still in its infancy — but as hardware becomes more accessible and agent-to-physical-world protocols mature, OpenClaw will increasingly power perception and control of the real world.

This repository aggregates projects, skills, and tutorials that bring OpenClaw into the physical realm.

---

## Table of Contents

| | | |
|---|---|---|
| [Single Board Computers](#single-board-computers) | [Microcontrollers](#microcontrollers) | [Voice \& Audio](#voice--audio) |
| [Vision \& Cameras](#vision--cameras) | [Home Automation \& IoT](#home-automation--iot) | [Robotics](#robotics) |
| [Displays \& HMI](#displays--hmi) | [Wireless Communication](#wireless-communication) | |

---

<details open>
<summary><h3 style="display:inline">Single Board Computers</h3></summary>

Running OpenClaw natively on single-board computers.

- [OpenClaw on Raspberry Pi](https://docs.openclaw.ai/raspberry-pi) - Official guide to running OpenClaw on RPi 4/5.
- [Raspberry Pi AI Agent Host](https://forums.raspberrypi.com/viewtopic.php?t=390769) - Fully agentic, self-hosted Docker-based development environment.
- [OpenClaw on Home Assistant](https://community.home-assistant.io/t/openclaw-clawdbot-on-home-assistant/981467) - Community guide for HA integration.
- [reComputer 一键部署/卸载 OpenClaw](https://github.com/baorepo/ee-datasheet-master) - One-click deploy/uninstall scripts for Seeed reComputer series.
</details>

<details open>
<summary><h3 style="display:inline">Microcontrollers</h3></summary>

Lightweight embedded implementations for MCU platforms.

- [MimiClaw](https://github.com/memovai/mimiclaw) - OpenClaw on ESP32-S3 — $5 hardware, pure C, no OS.
- [MimiClaw on XIAO S3](https://github.com/memovai/mimiclaw) - MimiClaw ported to Seeed Studio XIAO ESP32S3.
- [PicoClaw](https://github.com/sipeed/picoclaw) - RISC-V implementation, 10MB RAM, $10 board.
- [espclaw](https://github.com/baorepo/espclaw) - ESP32-based OpenClaw implementation with control demos.
- [nanobot](https://github.com/baorepo/nanobot) - Lightweight agent for embedded devices.
</details>

<details open>
<summary><h3 style="display:inline">Voice & Audio</h3></summary>

TTS, STT, microphones, and speaker systems for spoken interaction.

- [MimiClaw x reSpeaker](https://github.com/memovai/mimiclaw) - Voice-enabled AI assistant with reSpeaker (XVF3800) + ESP32S3.
- [OpenClaw Voice](https://openclawvoice.com/) - Browser-based voice chat with Whisper STT + ElevenLabs TTS.
- [Voice Call Plugin](https://docs.openclaw.ai/plugins/voice-call) - Twilio/Telnyx telephony integration.
- [ESP32 Voice Assistant](https://github.com/arpy8/ESP32_Voice_Assistant) - End-to-end conversational AI on ESP32.
- [ESP32 Agent Dev Kit](https://www.cnx-software.com/2025/01/24/esp32-agent-dev-kit-is-an-llm-powered-voice-assistant-built-on-the-esp32-s3/) - LLM-powered voice assistant on ESP32-S3.
</details>

<details open>
<summary><h3 style="display:inline">Vision & Cameras</h3></summary>

Computer vision, AI cameras, and visual perception systems.

- [reCamera Intellisense](https://github.com/SeeedStudio/reCamera) - Agent-friendly CLI/SDK for camera hardware with multi-camera support.
- [reCamera V2](https://github.com/SeeedStudio/reCamera) - Next-gen AI camera with scene understanding.
- [reCamera Gimbal](https://github.com/SeeedStudio/reCamera) - PTZ camera with gimbal control.
- [SenseCraft Watcher](https://github.com/SeeedStudio/SenseCraft-Watcher) - Protocol bridge for Seeed Watcher hardware.
- [VisionClaw](https://github.com/sseanliu/VisionClaw) - Meta Ray-Bans + Gemini Live + OpenClaw integration.
- [Hailo AI HAT](https://github.com/hailocom/hailo-ai-hat) - Raspberry Pi AI accelerator for local inference.
- [OpenClaw on Raspberry Pi with Hailo](https://www.hackster.io/psmooij/openclaw-for-robot-programming-pmsg-on-budget-d76a91) - Pi 5 + Hailo for local AI agents.
</details>

<details open>
<summary><h3 style="display:inline">Home Automation & IoT</h3></summary>

Home Assistant, smart home protocols, and IoT device integrations.

- [OpenClaw Home Assistant Add-on](https://github.com/techartdev/OpenClawHomeAssistant) - Native HA integration.
- [nanobot + reComputer RK + Local LLM](https://github.com/baorepo/nanobot) - Controlling IoT devices with local models.
- [SwitchBot Integration](https://openclaws.io/blog/openclaw-smart-home-iot) - Smart home control via SwitchBot.
- [DIY Home Assistant with RPi 5 + Ollama](https://www.reddit.com/r/LocalLLM/comments/1r84jou/diy_home_assistant_with_rpi_5_openclaw_ollama/) - Community guide for local AI home automation.
</details>

<details open>
<summary><h3 style="display:inline">Robotics</h3></summary>

Motor control, robot arms, and physical agent systems.

- [soarm-control](https://github.com/baorepo/soarm-control) - OpenClaw controlling SOArm 101 robotic arm with Nvidia Jetson.
- [Reachy Mini](https://github.com/pollen-robotics/reachy_ros) - Deploying OpenClaw on Reachy Mini humanoid robot.
- [OpenClaw for Robot Programming](https://www.hackster.io/psmooij/openclaw-for-robot-programming-pmsg-on-budget-d76a91) - Budget robot programming with Pi 5 + Hailo.
</details>

<details open>
<summary><h3 style="display:inline">Displays & HMI</h3></summary>

E-ink screens, LCD displays, and HMI devices.

- [SenseCraft HMI](https://github.com/SeeedStudio/SenseCraft-HMI) - Web content generator for e-ink displays.
- [OpenClaw 与墨水屏](https://github.com/baorepo/awesome-openclaw-hardware-projects) - Integrating OpenClaw with e-ink screens.
- [ESP32 Display Projects](https://www.xda-developers.com/cheap-esp32-display-projects-anyone-build/) - Cheap ESP32-based display projects.
</details>

<details open>
<summary><h3 style="display:inline">Wireless Communication</h3></summary>

LoRa, mesh networks, and off-grid communication protocols.

- [MeshClaw](https://github.com/baorepo/meshclaw) - Meshtastic integration for off-grid AI communication.
- [Meshtastic](https://meshtastic.org/) - Open-source mesh networking protocol for long-range communication.
</details>

---

## Contributing

Contributions welcome! Please read our [contributing guidelines](./CONTRIBUTING.md) before submitting PRs.

- Add only projects you've verified work
- Include clear descriptions
- Categorize appropriately
- Link to official docs when available

---

## Related Awesome Lists

- [awesome-openclaw](https://github.com/rohitg00/awesome-openclaw) — Main OpenClaw resource list
- [awesome-openclaw-usecases](https://github.com/hesamsheikh/awesome-openclaw-usecases) — Real-world use cases
- [awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) — 5,400+ community skills

---

## Stargazers

[![Stargazers over time](https://starcharts.vercel.app/seeed-projects.svg)](https://github.com/seeed-projects/awesome-openclaw-hardware-projects/stargazers)

---

## License

[![License: CC0](https://img.shields.io/badge/License-CC0-lightgrey?style=flat&style=flat)](LICENSE)

To the extent possible under law, contributors have waived all copyright and related rights to this work.
