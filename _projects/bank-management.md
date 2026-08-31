---
layout: page
title: Bank Management System
description: C Programming, Structs, Arrays, Procedural Programming
img: assets/img/8.png
importance: 2
category: work
---

Developed a Bank Management system entirely in C. This project focuses on the core principles of procedural programming, utilizing **Arrays of Structs** to manage client accounts locally in memory, and features a clean, interactive Terminal interface.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/9.png" title="Main Menu" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/10.png" title="Account Creation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/11.png" title="Transactions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Terminal Interface: Clear console outputs for the main dashboard, client registration, and standard banking operations.
</div>

To maintain data integrity during runtime, the system implements input validation for core banking transactions like Deposits, Withdrawals, and Transfers, ensuring account balances are updated accurately based on user input.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/12.png" title="Transaction Processing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/13.png" title="Structs Definition" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Console transaction execution (Left) and defined C Structs for managing account data in arrays (Right).
</div>

The project is designed by dividing the system into discrete functions for each feature. This includes searching for specific accounts, updating existing client details, and managing array indices to handle account deletions seamlessly.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/14.png" title="Search Functionality" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/15.png" title="Edit Records" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/16.png" title="Delete Account" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Additional functionalities: Searching client databases, modifying account details, and simulating account removal from the static array.
</div>

<div class="row mt-4">
    <div class="col-sm text-center">
        <a href="https://github.com/shereifDev/IEEE_azhar_DOCs/tree/main/C_language/graduation_project" class="btn btn-sm z-depth-1" role="button" target="_blank">
            <i class="fa-brands fa-github"></i> View Source Code on GitHub
        </a>
    </div>
</div>
