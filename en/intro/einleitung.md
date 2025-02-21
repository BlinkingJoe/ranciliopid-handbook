---
layout: default
title: Introduction PID System
parent: Introduction
grand_parent: EN - Manual
has_children: false
nav_order: 2
---

# Introduction PID System
{: .no_toc }

Contents

* TOC
{:toc}

## What is PID control good for?

A PID controller gives considerably better control of the water temperature in your espresso machine than the standard bimetal thermostat.

A mechanical thermostat will control the water temperature in your machine in a range of about 10° Celsius. The heater in the machine's boiler machine will heat up to the thermostat's cut out point. The thermostat shuts off the heating and switches on the 'ready' light on the machine.

Then the boiler cools down to the thermostat's cut in point. The 'ready' light goes off and the heater reheats up to cut off again. 

Between these two points, the machine is always signalling 'ready', although the water can be close to the cut out temperature, or just barely above cut in. Or pretty much anywhere in between.

In an espresso shot, water temperature is one of the critical parameters. Being off by just a degree C or two can make the difference between a sour shot (too cold), a burnt one (too hot) or a 'just right', well tasting shot. Not all coffee beans come out best at the exact temperature, either.

One way to a reproducible temperature is called temperature surfing. It entails flushing the machine to provoke the heater coming on, and then watching the ready lamp come back on when the thermostat cuts out. That way the machine is at a defined temperature and you can prepare the shot. Many people get annoyed by this - so were we.

The solution for small home use single boiler machines is to replace the thermostat with a PID controller that is able to hit the requested temperature within less than 1 °C. Our setup is quite capable to reach an accuracy of up to 0.1 °C. No need to hit the right time to pull a shot anymore - the right time is whenever the machine has initially warmed up.


## What can it do?

Our DIY PID has the following features:

* control the water temperature to within +/- 0.1 °C
* control brewing time as well as pre infusion in the "full expansion" build
* easy control via app for Android & iOS
* data monitoring via Grafana (web based) and MQTT (IoT) possible
* OTA (over the air) software updates
* PID software is open source: always free and customizable to your own needs
* compact build, fits into most small espresso machines
* the machine's stock cabling is not modified. The machine can always be restored to its original configuration
* Active community with fast support, always welcoming feedback and feature suggestions
 

## List of modified espresso machines

Our system was originally developed for the Rancilio Silvia, but works just as well in other machines. We know of successful upgrades to the following machines:


 * Rancilio Silvia V1 – V4
 * Rancilio Silvia E(co) V5 & V6
 * Gaggia Classic (9303) / Classic Pro (9480)
 * Lelit PL41 / PL42
 * La Pavoni EPL / Saeco Aroma / Gaggia New Classic (9403)
 * E61 single boiler (Bazzar A1 Livello, Fiorenzato Colombina)
 * E61 single boiler, dual use (Profitec Pro500)
 * Quick Mill Retro (0835) & Orione (3000)

## Differences PID Only vs. 'full expansion'

The minimal setup of our PID consists of the following components:
ID | Explanation
-|-
1 | Micro controller NodeMCU V2                 
2 | Temperature sensor TSIC 306                 
3 | Solid State Relais (SSR)                       
4 | Powersupply               
5 | Display (recommended, but optional) 
Heizung | Heating 

![Trockenaufbau](../../img/trockenaufbau.png)


There are two different levels of our system: PID only and full expansion. Over time there's been a few additional options, so the distinction is sometimes a bit less clear cut.


## Basic version (PID Only)

The basic version resembles a classic PID controller: the temperature sensor measures the temperature of the boiler (input) and forwards this information to the PID software running on the Micro controller (in our case NodeMCU). From here a control signal (output) is sent to the SSR which in turn switches the heating on and off. 

By that, the PID software achieves an exact regulation of the brewing temperature while the remainder of your machine stays untouched. MQTT, Display output and control via app are also possible in the basic version. 


## Extension to the basic version (PID Only Plus)

To give better temperature control during the brewing, you can add a sensor on to the machine's brew switch.


## Full expansion

Here, we go one step further and transfer control over the pump and the solenoid valve to the software too. This allows for additional flexibility by controlling three time intervals via the app:

* Pre-Infusion: the pump builds pressure and the three way valve applies water onto the portafilter

* Pause: the pump pauses, but the three way valve stays open. The pressure stays and allows for the coffee in the portafilter to soak. This can help reduce channeling in the coffee puck.

* Brew time: This is the normal extraction, brewing for the amount of time predefined in the app. A longer or shorter brewing time can improve the taste of the espresso, depending on the beans used and your personal preference.

There's a distinct change to the usage of the machine: the brewing switch that was previously controlling the extraction now starts the automated process. The extraction is stopped by the controller after the predefined time, even if the switch is still engaged.

We suggest to start with the basic version first. This gets you the biggest improvement to your coffee's taste. The full expansion allows for more flexibility, but requires a more complex modification of your machine.


## Full expansion Plus

This is where no compromises are required. You can add a scale to control the extraction time, as well as monitoring the brewing pressure using a pressure sensor.
