---
layout: page
title: AVR Electronic Calculator
description: ATmega32, 4x4 Keypad, 16x2 LCD, C Programming
img: assets/img/26.png
importance: 4
category: work
---

This project is a simple electronic calculator implemented using an AVR microcontroller. It processes standard arithmetic operations (`+`, `-`, `*`, `/`) by taking two-digit inputs and outputting results up to three digits.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/27.png" title="Calculator Hardware" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System Interface: Utilizing a 4x4 Keypad for numeric and operational inputs, and a 16x2 LCD for real-time display.
</div>

The system architecture relies on custom C headers (`keypad.h` and `LCD.h`), operating at an 8 MHz clock frequency (`F_CPU 8000000UL`). It handles runtime data conversion by mapping ASCII characters to decimal values (e.g., subtracting 48) to perform mathematical logic locally in memory.

* **Input Management:** Captures successive key presses via a polling mechanism (`KEYPAD_getKey()`) until valid numeric or operator inputs are registered.
* **Calculations:** Implements a procedural `switch` case structure to execute addition, subtraction, multiplication, and division based on the parsed operator array.
* **Output Formatting:** Dynamically formats the computed integer results to display hundreds, tens, and units sequentially on the 16x2 LCD.
* **System Reset:** Allows the user to reset the calculator and clear the display at any time by pressing the `A` key.
* **Power Requirements:** Designed to operate on a standard 5V DC power supply.

<div class="row mt-4">
    <div class="col-sm text-center">
        <video width="100%" controls class="rounded z-depth-1">
            <source src="{{ '/assets/video/calc.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/AVR-microcontroller/tree/main/MY-projects/Simple%20Calculator" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
