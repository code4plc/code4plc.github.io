---
layout: post
title: Problem with SET/RESET
---

Programming complex control systems requires knowing the execution context or state (for short) of the system. Knowing or preserving the state of the system usually means that we must remember that some events occurred or some actions took place in the past. Program variables are used to preserve state of the system. For example, if it is needed to remember that the temperature of cooling water reached critical value, variable _criticalTemperatureReached_ will be set to __TRUE__. When this information is no longer needed or is obsolete variable is simply reset to __FALSE__. So, what's the problem?

Automation world heavily relies on IEC61131-3 languages for writing control applications. Two most commonly used language LAD (and FBD) is modeled on electrical circuit diagrams being used for making control logic. Relays in control circuits need to be energized to activate other relays and make complex logic. Remembering user command is achieved, as shown on the picture: Two pushbuttons (or relay contacts) one normally opened (_NO_) and one normally closed (_NC_) are connected in series. When _NO_ contact is closed relay (_R_) is activatemd. In order to keep _R_ activated after _NO_ is released, parallel to _NO_ auxiliary contact of _R_ is connected. In this way _R_ will keep itself energized until _NC_ contact is opened. Then _R_ is reset. With arbitrary number of coils and contacts control circuits can be arbitrary complex and yet they all preserve two vital characteristics:

![Circuit Diagram](..\media\circuit_diagram.png)

- In order to keep _R_ energized current must flow through the coil. This means that engineering effort was focused on finding (and realizing) logic which will keep the coil energized. In other words, control is to find all cases (conditions) in which a state is active (coil energized)
- Information is preserved if current is flowing through the coil. On the other hand, if current is cut information is lost. Both establishing the current (__SET__) and cutting it (__RESET__) is made in the same circuit. It can not be that __SET__ in in one and __RESET__ is in another place.



Purpose of tis document is to outline basic issue with using SET/RESET 


