---
layout: page
title: IoT Health Monitoring
description: ATmega32, MQTT, Blynk, UART, ADC
img: assets/img/12.jpg
importance: 1
category: work
---

Developed an end-to-end IoT health monitoring system using ATmega32 to track patient vitals in real-time[cite: 2].

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="Project Hardware" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="Serial Communication" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="Blynk Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System architecture overview: Hardware integration with sensors (Left), VSPE serial communication setup (Middle), and real-time remote monitoring via Blynk dashboard (Right).
</div>

* Interfaced temperature and heartbeat sensors via ADC, utilizing UART and VSPE for reliable serial communication[cite: 2].
* Integrated MQTT protocol to transmit sensor data to the Blynk platform for remote monitoring, triggering alarms upon critical thresholds[cite: 2].
* [View Source Code on GitHub](https://github.com/shereifDev/NTI_IoT_Graduation_Project)
