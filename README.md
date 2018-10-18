---
description: >-
  BloomBus is an initiative to build a system for tracking and displaying the
  locations of shuttle buses owned and run by Bloomsburg University (and the
  C.G.A.) across the several loops that they run.
---

# What is BloomBus?

## History

![](.gitbook/assets/bloombus-logo%20%281%29.svg)

BloomBus began as a student project in 2015 through the Bloomsburg University ACM student chapter with a student, Dan Pany, who had the idea for the hardware that the tracking system would be based upon. He envisioned connecting an Adafruit GPS module to an Arduino microcontroller, in addition to an XBee radio transmitter, and using the 3 in tandem to receive GPS data, parse GPS data, and transmit GPS data \(respectively\). This system would also involve an XBee radio receiver connected over a USB connector to a server that would receive the GPS data, then upload it in a particular format onto a real-time database \(Google's Firebase\).

Another student, Rio Weber, began working with Pany on the BloomBus project primarily acting as the applications developer to provide the real-time database and user-facing application that displays the shuttles' coordinates. The 2 students conducted an independent study within the Digital Forensics program to work on a functioning prototype for this system. Their work is thoroughly documented in the document found [here](https://github.com/BloomBus/gitbook/blob/master/Pany%20%26%20Weber%20-%20BloomBus%20Project.pdf).

Unfortunately, the advertised range of 2 miles for the XBee radios was far greater than the experimental results found as Pany and Weber worked on conducting tests of the system. The results of these test can be found on page 13 of their aforementioned report.

In the 2018 Spring semester, another student, Nelson Maher, who had previous formal training with the PA National Guard in radio telecommunications and networking, had significant interest in the project, and proposed replacing the more expensive and radio-based system with a wifi based system utilizing ESP8266 chips — thumb-drive sized boards that have an onboard wifi chip and open source firmware that allows for the use of a framework called MicroPython. MicroPython allows for a subset of Python to be executed on the board's internal memory, and Maher quickly created a script that received in the same GPS data from the Adafruit module as before, parsed it, and uploaded it to Firebase. Thanks to the modularity of Weber's user-facing application, it continued to function exactly as previously expected. However, this system is intended to backpack off of the university's wireless network infrastructure, which is certainly spotty, especially along a route such as the campus loop where there is not a strong need for wireless coverage. This limitation also restricts the scope of the project's coverage to only the Campus Loop shuttle buses.

I, John Gibson, began working on this project in the 2018 Fall semester as an independent under the advisement of Dr. Robert Montante, with the goal of having a more complete prototype of the system that could be proposed to the C.G.A. for official adoption. 

My plan for having a more simplified and dependable system for this project to stand on would involve replacing the previous 2 proposed tracking hardware systems with instead using mobile phones assigned to each shuttle bus driver. The reasons for this proposal include:

* A mobile device can easily be plugged in to the shuttle bus and charged via the bus' 12V socket
* It provides an excellent GPS built into the phone
* Is capable of maintaining a significantly more dependable 4G connection with mobile networks
* Can provide an intuitive interface for the bus drivers can interact 

As part of my efforts to flesh out the software systems to create a prototype for the system, I have chosen to architect it broadly into 3 discrete applications:

1. BloomBus-Location-Tracker — A [Progressive Web Application](https://developers.google.com/web/progressive-web-apps/) \(PWA\) to be installed as apps on the mobile devices assigned to each shuttle driver, which when open provides an interface for selecting which loop the driver is currently driving, and displays the GPS position the device is providing. Using standard geolocation Web APIs, the device's position is published to Firebase every time the position is updated.
2. BloomBus-Client — Also a PWA, this is the user-facing app that allows students and other people on campus to select between shuttle loops and available shuttles, and see their locations on a map.
3. BloomBus-Server — A JavaScript based application that is run serverside, which acts as a monitor for the alterations on data within Firebase. For example, when a shuttle's position is updated, this application will start a timeout, where if that shuttle's position is not updated again with the timeout, its record will be removed from the database. This way, the client-side application only has to be concerned about displaying what is currently in the database. It will also monitor for proximity events using the [GeoFire](https://github.com/firebase/geofire-js) library for doing query's on the shuttles' updating coordinates. This way, when a shuttle nears a shuttle station, a record on the shuttle's reference in the database will be updated as a sort of "checkpoint" within the route.



