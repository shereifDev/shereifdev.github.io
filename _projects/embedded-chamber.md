---
layout: page
title: The Embedded Chamber
description: PIC18F4620, State Machine, HAL Drivers, Interactive Game
img: assets/img/17.png
importance: 3
category: fun
---

"The Embedded Chamber" is an interactive escape room game built on a **PIC18F4620 microcontroller**. It challenges players to solve a sequence of electronic puzzles using hardware interfaces, combining logic, embedded systems, and a strict C-based state machine.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/18.png" title="LCD & Keypad Interface" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/19.png" title="Logic Gates Puzzle" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/20.png" title="Power Bridge LEDs" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Game Interface: Players interact via a Keypad and LCD. Puzzles include Boolean logic challenges and manipulating LED states using physical push buttons.
</div>

The game's progression is strictly controlled by a **State Machine** architecture. It consists of 6 sequential stages, where each solved puzzle transitions the system to the next state, while incorrect answers trigger alarms via a Buzzer or randomly manipulate displays to confuse the player.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/21.png" title="Motor Lock Challenge" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/22.png" title="7-Segment Math Gate" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/23.png" title="Relay Cooling System" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Actuator Integrations: Calculating servo motor angles, solving 7-segment math equations, and activating a Relay to simulate unlocking the cooling system.
</div>

From a software engineering perspective, the project utilizes a highly modular **Hardware Abstraction Layer (HAL)**. Drivers for the LCD, Keypad, Motors, Relays, and 7-Segments were built from scratch, ensuring clean and reusable code across all puzzle functions (e.g., `Logic_Gate_Puzzle`, `Servo_Lock_Challenge`).

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/24.png" title="State Machine Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/25.png" title="Puzzle Structs" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Main loop State Machine execution (Left) and predefined puzzle logic stored in const Struct Arrays (Right).
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <video width="100%" controls class="rounded z-depth-1">
            <source src="{{ '/assets/video/ch.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/PIC-microcontroller/tree/main/MY-projects/Simple%20Game" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
