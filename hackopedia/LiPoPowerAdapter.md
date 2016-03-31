---
layout: page
title: Poweradapter für LiPo-Akkus
permalink: /hackopedia/LiPoPowerAdapter
---

## Der LiPo-Poweradapter

Lego mit 9V aus sechs 1,5V Batterien zu versorgen ist nicht schön. Die Alternative, sechs NiMH-Akkus zu verwenden ist schon besser, aber auch nicht gut, da man dann nur 7,2V zu Verfügung hat. Auch ist der Klotz aus diesen sechs AA-Zellen nicht sonderlich platzsparend. 

Im Modellbau sind LiPo-Akkus sehr populär, sie haben eine hohe Energiedichte und von den Strömen, die möglich sind, kann der Standard-Lego-Batteriekasten nur träumen. Daher schwebte mir eine  Energieversorgung aus solchen Akkus vor. Mein ursprünglicher Plan war die Verwendung von drei 18650-Akkus. Die sind dann allerdings doch etwas groß. 3S-Akkus aus dem Modellbau sind da (je nach Kapazität) deutlich kleiner. Also besorgte ich mir je einen solchen mit [1300mAh](http://www.ebay.de/itm/381493534405) und [1000mAh](http://www.ebay.de/itm/281745744579).

## Eigenschaften

Um die Akkus mit Lego nutzen zu können, brauche ich einen Adapter mit folgenden Eigenschaften:

* Betrieb am Balacer-Stecker der Akkus. (Für die richtige Power gibt es verschiedene Steckerformate, aber der Balancer-Anschluss ist normiert und für die von mir benötigten Ströme vollkommen ausreichend.)
* Ausgangsspannungen:
   * 9-12,6V (Nennspannung 11,1V) (Also volle Spannung aus dem 3S-Akku) 
   * 5V (zur Versorgung von Raspi und Arduino) über einstellbaren [Schaltregler](http://www.amazon.de/dp/B00Q8753KQ/)
   * 3-Pin-Stecker
* Ein/Aus-Schalter
* 10A-Sicherung (damit mir der Akku bei einem Kurzschluss nicht um die Ohren fliegt)
* Einzelüberwachung der drei Akkuzellen auf Unterspannung durch einen [LiPo-Tester](http://www.ebay.de/itm/191716987655).

## Entwicklung
Die Schaltung ließ sich sehr leicht mit [KiCad](http://kicad-pcb.org/) entwerfen. Der Schaltplan sieht so aus:

<img src="/images/LiPoPowerAdapterSchaltplan.png" alt="Schaltplan des LiPo-Poweradapters" width="600px" />

Und so das Layout der einseitigen Platine:

<img src="/images/LiPoPowerAdapterPCB.png" alt="Platinenlayout des LiPo-Poweradapters" width="600px" />

Das gesamte KiCad-Projekt liegt in meinen Github [Legohacks](https://github.com/HackingGulliver/LegoHacks/tree/master/hardware/KiCad/LiPoPowerAdapter).

Das Layout habe ich auf Folie ausgedruckt und damit die einseitig mit Photolack beschichtete Platine belichtet. Unter meiner Gesichtsbräuner-UV-Lampe betrug die Belichtungszeit 1 Minute 30 Sekunden. Nachddem die Platine in NaOH entwickelt war, ging es ins Natriumpersulfat im Ätzgerät.

Das Bild zeigt die fertige Platine, die bedruckte Folie und das Leiterplattenmaterial (mit Schutzfolie).

<img src="/images/LiPoAdapter1.JPG" alt="Belichtung" width="600px" />

Hier alle Einzelteile, die nun zu verlöten waren. (Es fehlt der senkrecht stehende Adapter für den LiPo-Tester.)

<img src="/images/LiPoAdapter2.JPG" alt="Vor dem Löten" width="600px" />

Um in der Fläche Platz zu sparen, habe ich mich für eine vertikale Bauweise entschieden. Dies bot sich an, da der Schalter und die Sicherung für sich alleine schon recht hoch sind. Somit schwebt der LiPo-Tester über dem Spannungsregler. 

<img src="/images/LiPoAdapter3.JPG" alt="Adapter von oben" width="600px" />

Der LiPo-Tester ist nur gesteckt und kann daher auch noch an anderer Stelle verwendet werden.

<img src="/images/LiPoAdapter4.JPG" alt="Adapter ohne LiPo-Tester" width="600px" />
<img src="/images/LiPoAdapter5.JPG" alt="Adapter von der Seite" width="600px" />

Mit Akku ist das Ganze dann komplett. Der LiPo-Tester zeigt, dass alle drei Zellen noch im grünen Bereich sind. Am Ausgang können (von unten nach oben) GND, +5V und +11,1V entnommen werden.

<img src="/images/LiPoAdapter6.JPG" alt="Adapter mit Akku" width="600px" />


## Betrieb

Die Akkus werden über ihren Balancer-Anschluss am Adapter betrieben. 

Das Schöne an der Sicherung ist auch, dass man sie entnehmen kann und über die Kontakte den Strom messen kann, der von der angeschlossenen Schaltung aufgenommen wird. Im Leerlauf zieht der Schaltregler ca. 6,6 mA. Mit Raspi 3 werden bei ruhendem Desktop ca. 150mA gezogen. Mit Funkmaus und Tastatur sind es knapp 180mA. Bei der zusätzlichen Wiedergabe eines YouTube-Videos im Browser sind wir bei ca. 280 mA. Wenn der Raspi mit einer Mathematica-Demo befeuert wird (>80% Last) kommen knapp 500mA zusammen. Das bedeutet, dass man mit dem kleinen 1000mAh-Akku gut 3 Stunden Video schauen kann oder 2 Stunden lang Mathematica-Demos laufen lassen kann.

Der Schalter schaltet den Stromfluss über die GND-Leitung aus. Damit werden die LEDs des LiPo-Testers ausgeschaltet. Trotzdem zieht dieser noch einen minimalen Strom (wahrscheinlich über die anderen Balancer-Leitungen). Auch erlaubt der LiPo-Tester bei ausgeschaltetem Schalter einen geringe Stromentnahme am Ausgang, der normalerweise die Akkuspannung führt. Es ist also bei längerer Pause besser, den LiPo-Tester oder den Akku abzuziehen.
