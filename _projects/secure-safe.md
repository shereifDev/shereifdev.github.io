---
layout: page
title: Secure Safe System
description: AVR ATmega32, EEPROM Memory, Keypad, Security Lockout
img: assets/img/28.png
importance: 5
category: work
---

Developed a robust hardware-based Secure Safe System utilizing an **AVR ATmega32** microcontroller. This project showcases advanced embedded systems security concepts, including non-volatile memory management, real-time input masking, and automated hardware lockouts.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/29.png" title="Initial Boot" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/30.png" title="Confirm Password" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/31.png" title="EEPROM Storage" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    First-Run Sequence: The system detects uninitialized memory, prompting the user to set and confirm a new 4-digit password.
</div>

The core security relies on the microcontroller's internal **EEPROM**. The system checks a specific status location (`0x50`) on boot. If it reads `0xFF` (uninitialized), it triggers the setup mode. Once the user enters and confirms identical passwords, the 4-digit code is safely written starting at address `0x20`, and the status flag is updated to prevent overriding on subsequent reboots.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/32.png" title="Visual Masking" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/33.png" title="Authentication" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Security features: Real-time input masking using LCD cursor shifting to hide keypad entries.
</div>

To ensure physical security during operation, the system features a dynamic masking algorithm. When a key is pressed, the character is displayed on the 16x2 LCD for exactly 300ms for user confirmation, before executing a `SHIFT_CUR_LEFT` command and replacing it with an asterisk (`*`).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/34.png" title="Attempt Tracking" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/35.png" title="System Lockout" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/36.png" title="Access Granted" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Anti-Brute Force mechanism: Deducting tries (Left), 9-second timer lockout (Center), and successful override (Right).
</div>

The system includes multiple layers of operational security and feedback:
* **Anti-Brute Force Lockout:** The system tracks authentication failures. If `MAX_TRIES` (3 attempts) is reached, a strictly timed `for` loop forces a 9-second hardware lockout, displaying a countdown on the LCD and ignoring all keypad inputs.
* **Master Reset Protocol:** As a fallback, entering a hardcoded sequence (`0000`) formats the EEPROM status flag, forcing the system to reboot into the initial setup stage.
* **Hardware Feedback:** Direct port manipulation controls the Red LED (Locked) and Green LED (Verified/Open).

<div class="row mt-4">
    <div class="col-sm text-center">
        <video width="100%" controls class="rounded z-depth-1">
            <source src="{{ '/assets/video/ss.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/AVR-microcontroller/tree/main/MY-projects/SAFE" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
