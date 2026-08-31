---
layout: page
title: Digital Clock & Timer System
description: ATmega32, Multiplexed 6-Digit 7-Segment, Timer2 Interrupts
img: assets/img/37.png
importance: 6
category: work
---

Developed a multi-functional digital clock using an AVR ATmega32 microcontroller, featuring a real-time clock, stopwatch, and countdown timer managed via hardware interrupts and multiplexed displays.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/38.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/39.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/40.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/41.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/42.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/43.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hardware setup showcasing the 6-digit 7-segment display, state control buttons, and matrix keypad integration.
</div>

**Operating Modes & Hardware Interface**

| Mode | Indicator | Controls | Functionality |
|---|---|---|---|
| Clock | None | PA7 (Set) + Keypad | Standard 24-hour timekeeping format (HH MM SS). |
| Stopwatch | Green LED | PA6 (Enter), PA4 (Pause) | Counts up continuously to a maximum of 23:59:59. |
| Timer | Red LED | PA3 (Enter) + Keypad | Countdown execution triggering a buzzer alarm upon completion. |

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/44.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/45.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/46.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/47.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/48.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/49.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visual state indicators, buzzer alarm activation, and multiplexing logic execution captured during runtime.
</div>

**Firmware Architecture**

* **Interrupt Service Routine (ISR):** Employs Timer2 overflow interrupts to generate precise 1-second ticks, ensuring accurate background timekeeping regardless of the active operational mode.
* **Display Multiplexing:** Drives the 6-digit 7-segment module by rapidly cycling control pins (`PC0` to `PC5`) with a precise 5ms delay per digit, outputting decoded BCD values sequentially on `Port B` to eliminate visual flicker.
* **Input Handling:** Integrates a 4x4 matrix keypad for setting specific HH:MM:SS values dynamically, alongside hardware-debounced tactile switches (PA3, PA4, PA6, PA7) for executing immediate state transitions.
* **State Machine:** Seamlessly transitions execution contexts between the clock, stopwatch, and timer logic without halting or resetting the underlying system timers.

<div class="row mt-4">
    <div class="col-sm text-center">
        <video width="100%" controls class="rounded z-depth-1">
            <source src="{{ '/assets/video/RTC.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/AVR-microcontroller/tree/main/MY-projects/RTC" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
