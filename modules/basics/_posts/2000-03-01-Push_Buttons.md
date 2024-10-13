---
title: Digital Inputs
---

<div class="header1" id="top" markdown = "1"># Digital Inputs
</div>

<div class="header2" markdown = "1">## Onderdelen
</div>

Voor deze opdracht heb je de volgende onderdelen nodig:

- rode LED x 1
- Push Switches x 2
- 220 ohm weerstand x 1

<div class="header2" markdown = "1">## Push Switches
</div>

Switches zijn heel eenvoudige onderdelen. Wanneer je een knop indrukt, maak je contact zodat de elektriciteit door kan stromen. De kleine switches die we hier gebruiken hebben vier aansluitpunten, wat een beetje verwarrend kan zijn.

![image]({{ site.baseurl }}/img/push_button.png)

Je hebt maar twee van deze punten nodig, maar ze moeten wel aan de tegenovergstelde kant van de switch zitten. De aansluitpunten die naar mekaar wijzen, zijn al gekoppeld aan mekaar.

<div class="header2" markdown = "1">## Schematic
</div>

![image]({{ site.baseurl }}/img/button-circuit.png)

<div class="header2" markdown = "1">## Code
</div>


Je gaat nu zelf de code schrijven voor deze opstelling. Dit keer gaan we de pins waarop de buttons zijn aangesloten als **input** gebruiken, in plaats van als **output**, zoals we eerder deden. Daarom gebruiken we andere argumenten voor het instellen van de pinnen:

```python
button = Pin(25, Pin.IN, Pin.PULL_UP)
```

- **25** is het GPIO-nummer van de pin die je wilt gebruiken.
- **Pin.IN** geeft aan dat deze pin als input wordt gebruikt.
- **Pin.PULL_UP** zorgt ervoor dat de pin standaard op een hoge waarde (1) staat, totdat de button wordt ingedrukt.

### Wat is PULL_UP?

**PULL_UP** bepaalt hoe de pin wordt ingesteld als er geen signaal is. Dit betekent dat de pin standaard is verbonden met een hoge spanning (3.3V) via een interne weerstand. Wanneer je de button indrukt, maak je verbinding met de aarding (GND), waardoor de pin een lage waarde (0) krijgt. Dit is de meest gebruikelijke manier om buttons aan te sluiten.

Je zou de buttons ook op een 3V-connector kunnen aansluiten en in dat geval gebruik je **PULL_DOWN**. Dan staat de pin standaard laag (0) en krijgt hij een hoge waarde (1) wanneer de button wordt ingedrukt.

### Hoe werkt het?

- Bij **PULL_UP**:
  - Als de button **niet** is ingedrukt, leest de pin **1** (hoog).
  - Als de button **wel** is ingedrukt, leest de pin **0** (laag).
  
- Bij **PULL_DOWN** werkt het precies andersom:
  - Niet ingedrukt = waarde **0** (laag).
  - Ingedrukt = waarde **1** (hoog).

### Je opdracht:

- Kies 3 verschillende digitale pinnen op je Arduino. Stel 2 daarvan in als **input** (voor de buttons) en 1 als **output** (voor de LED).
- Gebruik één button om de LED aan te zetten en de andere button om de LED uit te schakelen.

