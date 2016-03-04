---
layout: page
title: Ideenseite
---

Folgendes möchte ich noch bauen:

* Lego-Powerpack
  * Spannungsversorgung bestehend aus 3 18650 LiIon-Akkus (11,1V - 12,6V)
  * Ladezustandsanzeige zur Einzelüberwachung der Akkus (z.B. [LED](http://www.ebay.de/itm/2S-3S-Lipo-Low-Voltage-Checker-Akku-Tester-Warner-Buzzer-Alarm-Anzeiger-Pieper-/191716987655?hash=item2ca3391307:g:iFYAAOSwT5tWIJJP) oder mit [Anzeige](http://www.ebay.de/itm/Buzzer-1S-8S-Lipo-Alarm-Warner-Schutz-Checker-Voltage-Buzzer-Pieper-1S-2S-3S-/181874441115?hash=item2a588fbb9b:g:LpMAAOSwFnFV-4RB))
  * Akkus werden getrennt in externem Ladegerät geladen
* Motortreiber-Shield für normale Elektromotoren
* Motortreiber-Shield für Schrittmotoren
* LED-Treiber-Shield für viele LEDs, einzeln ansteuerbar (z.B. für Fahrzeugbeleuchtung)
  * Ansteuerung über Shift-Register74HC595, Treiber ULN 2803
  * Jeweils einzelne Platine für je acht LEDs in der gleichen Farbe mit Vorwiderständen. Serielle Ausgang zur nächsten Platine.
* Funkfernsteuerung auf Basis 433MHz
* Steuerung über PS1 oder PS3-Controller
  * Siehe [PSX_Analog Library](https://github.com/kiram9/Arduino_PSX_Analog)

