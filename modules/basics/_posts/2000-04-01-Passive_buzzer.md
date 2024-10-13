---
title: Active Buzzer
---

<div class="header1" id="top" markdown = "1"># Buzzer
</div>

<div class="header2" markdown = "1">## Onderdelen
</div>

Voor deze opdracht heb je de volgende onderdelen nodig:

- Passieve buzzer x 1
- Push Switch x 1

<div class="header2" markdown = "1">## Buzzers
</div>

Elektronische buzzers worden gevoed door een gelijkstroom (DC) en zijn uitgerust met een geïntegreerd circuit. Ze worden veel gebruikt in computers, printers, kopieerapparaten, alarmsystemen, elektronisch speelgoed, elektronische apparaten in auto's, telefoons, timers en andere elektronische producten voor geluidstoepassingen. Buzzers kunnen worden onderverdeeld in actieve en passieve varianten. Houd de pinnen van twee buzzers omhoog. De buzzer met een groene printplaat is een passieve buzzer, terwijl de andere, die omgeven is door zwart tape, een actieve buzzer is.

Het verschil tussen de twee is dat een actieve buzzer een ingebouwde oscillatiebron heeft, waardoor hij geluid genereert zodra hij van stroom wordt voorzien. Een passieve buzzer heeft zo'n bron niet en zal geen geluid maken als hij met een gelijkstroomsignaal wordt gevoed. In plaats daarvan moet je blokgolven gebruiken met een frequentie tussen 2K en 5K om hem te laten werken. De actieve buzzer is vaak duurder dan de passieve vanwege de meerdere ingebouwde oscillatiecircuits.

In deze oefening gebruiken we een passieve buzzer. 

![image]({{ site.baseurl }}/img/passive_buzzer.png)

<div class="header2" markdown = "1">## Schematic
</div>

![image]({{ site.baseurl }}/img/circuit_passive_buzzer.png)

<div class="header2" markdown = "1">## Code
</div>

Een passive buzzer heeft een blokgolf nodig. Die kunnen we maken via PWM. De Instrument class hieronder doet precies dat. Via de play functie kunnen we een frequentie en een duur meegeven en zo speel je dan een toonhoogte. Een buzzer is geen speaker van hoge kwaliteit, dus je kies best geen extreme frequenties. Tonen tussen de 300Hz en 800Hz zouden geen probleem mogen zijn. De duur geef je in in milliseconden.


```python
import time
import random
from machine import PWM, Pin

class Instrument:
  def __init__(self, pin):
    self.buzzer = PWM(Pin(pin))

  def play(self, frequency, duration):
    if frequency == 0:
      time.sleep_ms(duration)
    else:
      self.buzzer.freq(frequency)
      self.buzzer.duty_u16(32768)
      time.sleep_ms(duration)
      self.buzzer.duty_u16(0)
```

<div class="header2" markdown = "1">## Experimenteer
</div>

Laat de speaker spelen met behulp van deze class. Je hebt verschillende mogelijkheden:

- Je kan een random functie gebruiken om frequenties te kiezen
- Je kan opzoeken welke frequenties je nodig hebt voor je melodie naar keuze en die in een list steken
- Je kan opzoeken hoe je MIDI *(Een standaard waarin elke noot die in traditionele muziek gebruikt wordt, een nummer krijgt.)* omzet naar een frequentie met behulp van python.




