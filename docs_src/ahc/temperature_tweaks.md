---
hide:
  - toc
---
# 🎚️ Temperature Tweaks

## 🛑 Off Instead Of Eco

If your heating schedule is *off* or nobody triggers your presence sensor the automation sets the eco temperature. Enable this option to turn off the climates instead.

## ⬇️ Min Instead Of Off

If the automation detects open windows or the winter mode is turned *off* the automation sets the thermostats to *off*. Enable this option to set the eco temperature instead.

## 🇫 Fahrenheit

If Fahrenheit is your unit enable this option.

!!! warning "Experimental"

    This feature is still untested. If you experience any issues, please let me know.

## ↩️ Reset Temperature

Enable this option to reset your temperature entities after a switch between eco and comfort temperature.

``` mermaid
sequenceDiagram
  autonumber
  ECO->>COMFORT: Eco Temperature Reset
  COMFORT-->>ECO: Comfort Temperature Reset
```

## ↕️ Off If Above / Below Room Temperature

If the room temperature hits the target temperature your climates get turned *off*. For HVAC Mode *Cool* the room temperature must be lower or equal before the climates get turned *off*.


## 🧪 Physical Temperature Change / Sync

If you want to synchronize a manually set temperature with your other thermostats or temperature entities, you can activate this option.

!!! warning "Experimental"

    This feature has several side effects. It's not recommended to enable this option in a combination with generic calibration or aggressive mode.