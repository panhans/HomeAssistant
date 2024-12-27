---
hide:
  - toc
---
# 🚶 Presence Detection

With presence detection, you can set the comfort temperature if presence or movement is detected. Furthermore, you can also integrate your own binary sensors and use them as presence sensors.

!!! warning "An overview explaining the logic will follow later in the documentation."

## 🚶 Presence Sensor

Here you can specify your presence entity. This can be an *input boolean* or a *binary sensor*.

!!! info "Some presence sensors need to be debounced since they are triggering too often. Have a look in the Helpful Snippet Section."

## ⏲️ Presence Sensor Schedule

Mit einem Präsenz Schedule kannst du zeitliche Bereiche festlegen, an denen die Präsenzerkennung zum tragen kommen darf.

<figure markdown="span">
  ![Image title](images/ahc/presence_scheduler.png){ width="300" }
  <figcaption>Example Presence Schedule - Blue means presence could be detected</figcaption>
</figure>

## ⏳ Presence Reaction On Time

To prevent the comfort temperature from being set if you only briefly enter the room, you can set a time tolerance here. The sensor must continuously detect presence for this period for the comfort temperature to be set.

## ⌛ Presence Reaction Off Time

To prevent the eco temperature from being set immediately when you briefly leave the room, you can set a period here during which no presence must be detected for the temperature to fall back to the eco temperature.