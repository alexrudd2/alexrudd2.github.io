---
layout: post
title:  "Voltage and current signals"
date:   2023-10-10 20:00:00 -0500
categories: voltage, current, signal, 4-20mA
---

### Voltage signals (discrete)
Voltage signals are a fundamental way of transmitting information through a pair of wires.  A device on one end creates a voltage differential between two wires, and a device on the other end measures it.  The measuring device can be as simple as a multimeter, or even a small light.  Both ends agree on what different voltages mean.  For instance, `0V` = `OFF` and `5V` = `ON`.  This works reasonably well for discrete signals.

### Voltage signals (continuous)
Voltage signals can also be used for a continuous range of values.  For instance, `0V` = `0%` and `5V` = `100%`.   Any intermediate voltage can be interpreted between the minimum and maximum values.  In this example, `2V` would be `40%` (`(2V - 0V)/(5V - 0V) * (100% - 0%)`).

There's a slight problem with this system - how can you distinguish between `0%` and a broken wire, which would also be `0V`?  This can be avoided by using a signal other than `0V`, which is called a "live zero."  For instance, `0V` = `ERROR`, `1V` = `0%`, and `5V` = `100%`.  With the live zero example, `2V` would be `25%` (`(2V - 1V)/(5V - 1V) * (100% - 0%)`).

Another problem is the measurement error over distances.  Since wires have resistance, there will be a slight voltage drop from one end to another, degrading the signal.  Also, voltage signals are quite sensitive to "induced voltages" from nearby electrical equipment.  These are fundamental problems with voltage signals, and they should be avoided if possible.  Past a certain scale, voltage signals are downright awful.

![Use current signals, not voltage](/assets/voltage_signals.png)


### Current signals (continuous)
Current signals solve many of the problems of voltage signals.  By far the most common signal for process control is `4-20mA`, which already uses a live zero.  Current signals also don't drop over long distances, and are not very susceptible to induced voltage.  Problem solved!

The math remains the same.  For instance, if `4mA` = `100 °C` and `20mA = 200 °C`, then `12mA = (12mA - 4mA)/(20mA - 4mA) * (200 - 100°C) + 100°C = 150°C`

Current signals are superior to voltage signals and should be used whenever possible.
