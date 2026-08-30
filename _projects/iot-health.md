---
layout: page
title: IoT Health Monitoring
description: ATmega32, MQTT, Blynk, UART, ADC
img: assets/img/7.png
importance: 1
category: work
---

Developed an end-to-end IoT health monitoring system using ATmega32 to track patient vitals in real-time . Below is a showcase of the hardware components and system architecture.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.png" title="Temperature Sensor" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2.png" title="Heartbeat Sensor" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.png" title="ATmega32 MCU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hardware components: Interfaced temperature and heartbeat sensors via ADC for reliable data acquisition .
</div>

The core of the system relies on robust communication. Utilizing UART and VSPE was crucial for reliable serial communication between the microcontroller and the local gateway before pushing to the cloud. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/4.png" title="System Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Integrated MQTT protocol to transmit sensor data to the Blynk platform for remote monitoring.
</div>

Finally, the system is designed to trigger immediate alarms upon reaching critical thresholds, ensuring rapid response to any irregularities in patient vitals.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/5.png" title="Serial Terminal" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.png" title="Blynk App" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Local serial terminal output (Left) alongside the mobile Blynk dashboard interface (Right).
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <video width="100%" controls class="rounded z-depth-1">
            <source src="{{ '/assets/img/p1.mp4' | relative_url }}" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/NTI_IoT_Graduation_Project" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
