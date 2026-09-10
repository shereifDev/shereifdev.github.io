---
layout: page
title: Scalable Agricultural Edge Node with Cloud-Native FOTA
description: ESP32, Custom PCB, RS485/Modbus, Docker, GitHub Actions CI/CD, Blynk IoT
img: assets/img/28.png
importance: 1
category: work
---

**Client:** Syntax-IoT &nbsp;|&nbsp; **Role:** IoT Engineering Intern &nbsp;|&nbsp; **Stack:** ESP32, C/C++, PCB Design (EasyEDA), Docker, GitHub Actions, Blynk IoT

An industrial-grade, ESP32-based agricultural edge node built around a custom PCB, paired with a fully automated Cloud-Native Firmware-Over-The-Air (FOTA) pipeline. The project bridges low-level embedded hardware design with modern DevOps practice, removing the need to physically visit a field device to update its firmware.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/28.png" title="Agricultural Edge Node - PCB 3D Render" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    3D render of the custom Agri-Edge-Node PCB (v1.0) — ESP32-WROOM-32E module, RS485 terminal, solar and battery inputs, isolated control block.
</div>

### The Problem

Syntax-IoT operates monitoring nodes across remote agricultural and aquaculture sites. At scale, two things become bottlenecks:

* **Manual firmware flashing** — sending a technician to physically reflash a microcontroller on every field unit is slow and expensive.
* **Field downtime** — every on-site intervention takes the node offline and interrupts data collection.

The goal was a self-contained edge device that can be updated remotely, safely, and automatically — with zero site visits.

### System Architecture

The node follows a "Hybrid Edge Architecture": embedded hardware for sensing and control, and a cloud-native pipeline for build, release, and OTA delivery.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/31.png" title="Hardware Architecture Block Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Block-level view of the four subsystems: power supply, core logic, industrial interface, and isolation barrier.
</div>

---

## Hardware Engineering

The board was fully designed from schematic to Gerber in EasyEDA and fabricated as a 4-terminal, solar/battery-powered field unit.

* **Core:** ESP32-WROOM-32E (N4, 4MB) for Wi-Fi connectivity and dual-core processing.
* **Industrial sensing:** SP3485EN-L/TR RS485 transceiver for Modbus RTU communication with industrial sensors.
* **Electrical isolation:** three PC817C-S optocouplers isolate the RS485 side from the ESP32 logic domain to protect against field-side electrical noise.
* **Power management:** TP4056 charge controller with an 18650 Li-ion cell, a solar input, and an HT7333 LDO regulating down to a clean 3.3 V rail — the node is fully off-grid capable.
* **Housekeeping:** boot/reset push-button, status LEDs (ESP + solar charge), and a dedicated programming header (J_PROG) for UART flashing.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/29.png" title="Full Schematic" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/30.png" title="PCB 3D Render - Top View" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: complete schematic split into Power Management and Control blocks. Right: top-down 3D render of the routed PCB.
</div>

**Key components (from the released BOM):**

| Ref. Designator | Part | Function |
|---|---|---|
| U1 | ESP32-WROOM-32E-N4 (4MB) | Main microcontroller / Wi-Fi |
| U3 | TP4056 | Li-ion battery charge management |
| U2 | HT7333-A | 3.3V LDO regulator |
| U4 | SP3485EN-L/TR | RS485 transceiver |
| U5–U7 | PC817C-S | Opto-isolation (x3) |
| U11 | B0303S-1WR3 | Isolated DC-DC converter |

<div class="row mt-4">
    <div class="col-sm text-center">
        {% include figure.liquid loading="eager" path="assets/img/34.png" title="PCB 3D Render - Angle View" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Angled render showing the solar/battery/RS485 terminal blocks alongside the isolation barrier components.
</div>

---

## Firmware

The firmware (C/C++, ESP-IDF/Arduino core) handles Wi-Fi connectivity, Modbus polling over RS485, threshold checks, telemetry publishing to Blynk, and — critically — checking for and applying OTA updates on every cycle.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/32.png" title="Firmware Flowchart" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Runtime flow: boot → Wi-Fi/provisioning → Modbus read → telemetry push → OTA check → flash to inactive partition → reboot.
</div>

Updates are written to the inactive OTA partition (dual-bank) so a failed update never bricks a deployed unit — the device can always fall back to the last known-good firmware.

---

## DevOps & Cloud-Native FOTA Pipeline

This is the part that removes the human from the update loop. Every firmware commit triggers an automated build-and-release pipeline:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/33.png" title="CI/CD Pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    GitHub push → GitHub Actions webhook → isolated Docker build container → PlatformIO/ESP-IDF compile → firmware.bin → Blynk Air → wireless FOTA push to the node fleet.
</div>

1. **Version control** — firmware commits pushed to GitHub.
2. **CI trigger** — GitHub Actions spins up an isolated Docker container on every push.
3. **Reproducible build** — PlatformIO/ESP-IDF compiles the firmware inside the container, so builds never depend on a developer's local machine setup.
4. **FOTA distribution** — the resulting `firmware.bin` is pushed to Blynk Air, which handles secure Over-The-Air delivery to every node in the field.

---

## Outcome

* Fully routed and fabricated custom PCB (schematic, layout, Gerbers, and BOM).
* Assembled, functional ESP32 edge node prototype.
* Modular C/C++ firmware with Modbus RTU acquisition and dual-bank OTA support.
* Working CI/CD pipeline (GitHub Actions + Docker) producing reproducible firmware builds.
* Live Blynk dashboard for telemetry and remote FOTA management.

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/SyntaxIoT_Gateway" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
