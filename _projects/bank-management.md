---
layout: page
title: Bank Management System
description: C Programming, Static Arrays, Structs, Colored Terminal UI
img: assets/img/8.png
importance: 2
category: work
---

Developed a fully functional Bank Management system entirely in C. This project focuses on procedural programming, utilizing **Static Arrays of Structs** to manage client accounts locally in runtime memory, completely independent of external databases.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/9.png" title="Main Menu" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/10.png" title="Admin & User Windows" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/11.png" title="Customer Data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System Architecture: Separation of privileges (Admin vs. User windows) and detailed customer data structures including National ID, DOB, and Account Status.
</div>

A standout feature of this project is the **Colored Terminal UI**. By defining custom C macros for ANSI escape codes (e.g., `__yellow__`, `__green__`, `__red__`), the console provides an interactive and visually organized experience for the user.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/12.png" title="Account Deletion Logic" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Memory Management: Efficiently deleting accounts by shifting array elements dynamically and decrementing the global index, preventing memory fragmentation.
</div>

The system ensures robust transaction processing (Deposits, Withdrawals, and Transfers). It includes strict validations to check if an account is "Dormant" or "Active", prevents negative cash inputs, and securely updates balances across the array elements.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/13.png" title="Money Transfer Logic" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/14.png" title="Security & Authentication" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Handling sender/receiver balance updates safely (Left) and custom password matching logic (Right).
</div>

The codebase is highly modular, heavily utilizing `switch` cases, iterative loops, and string manipulation functions (`strcmp`, `strcpy`, `strcspn`) to handle user inputs securely.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/15.png" title="Change Password" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/16.png" title="Account Status" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Additional functionalities: Secure password resetting and toggling account accessibility states.
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/IEEE_azhar_DOCs/tree/main/C_language/graduation_project" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
