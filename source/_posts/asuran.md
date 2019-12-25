---
title: Asuran
date: 2016-11-13 18:22:46
categories: 
- Projects
cover_index: /images/asuran/index.jpg
cover_detail: /images/asuran/banner.jpg
---

Location-based insurance premium prediction implemented as android application. The app uses geofencing to locate the user. The insurance premium data for every location in a city will be various depends on its condition (e.g. the locations with higher risk will have higher premium). Users can register themselves in on-demand manner when they are approaching the location with high risk.
All locations are updated in near real-time.

An MQTT back-end is used as a message broker to publish locations information and their premium that can be varied over time.

<figure class="images-row">
<img style="display: inline;" src="/images/asuran/2.png" width="200"> <img style="display: inline;" src="/images/asuran/3.png" width="200"> <img style="display: inline;" src="/images/asuran/6.png" width="200">
<figcaption>
Android application Screenshots: 1. Login screen. 2. Initialization screen shows three important locations of the user (home, last location where he activates the insurance for car, and last location where he activates the life insurance). 3. Predictive locations where the risk might occur. The red color shows the highest risk.
</figcaption>
</figure>

<hr>
- Date: October 2016
- Team: Muhammad Abduh, Rian Josua Masikome, Galih Gilang Wicaksono
- A Project of Zurich Insurhack 2016
