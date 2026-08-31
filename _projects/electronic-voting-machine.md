---
layout: page
title: Electronic Voting Machine
description: AVR ATmega32, 16x2 LCD, Internal Pull-ups, Software Debouncing
img: assets/img/50.png
importance: 7
category: work
---

Developed a 4-channel Electronic Voting Machine (EVO) using an AVR ATmega32 microcontroller. The system accurately tallies votes for four distinct candidates/options, utilizing direct hardware interfacing and robust software debouncing to ensure counting precision.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/51.png" title="Welcome Screen" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/52.png" title="Initial Counters" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/53.png" title="Active Voting" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System progression: From the initial boot prompt to tracking active votes for all four candidates simultaneously.
</div>

**Hardware Configuration & Memory Optimization**
* **Input Interface:** 5 tactile push buttons connected directly to `PORTD` (PD0 to PD4). To minimize external components, the ATmega32's internal pull-up resistors are enabled via software (`pullUpEnable('D',i)`).
* **Display Interface:** A 16x2 LCD operates in 4-bit mode to save microcontroller pins, mapped to `PORTB` (PB0-PB2 for control, PB4-PB7 for data).
* **ASCII Conversion:** Integer vote counts are converted to printable characters dynamically during runtime by adding `48` to the integer value, avoiding the overhead of heavy library functions like `sprintf()`.

**Software Debouncing & Logic Processing**
Mechanical button bounces often cause false multi-clicks. This system implements strict software debouncing by registering a logic `0` (due to pull-ups), applying a `150ms` delay, and verifying the logic `0` again before incrementing the variable.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/54.png" title="System Reset" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/55.png" title="Debouncing Logic" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/56.png" title="Reset Hex Clearing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System reset execution (Left) and source code excerpts highlighting the software debouncing and LCD residual character clearing (`0x20`).
</div>

**Dynamic LCD Formatting & Residual Data Clearing**
When a candidate's votes exceed 9, the code mathematically extracts the tens and units (`A/10` and `A%10`). A critical detail is handled during the system reset: if a counter drops from a two-digit number (e.g., 15) back to 0, the second digit remains on the LCD. The reset logic brilliantly sends a hex space character (`0x20`) right after the zero to overwrite any residual numbers on the screen.

<div class="row mt-4">
    <div class="col-sm text-center">
        <video width="100%" controls class="rounded z-depth-1">
            <source src="{{ '/assets/video/EVO.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/AVR-microcontroller/tree/main/MY-projects/EVO" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
