---
hide:
  - toc
---
# 😡 Aggressive Mode

Some thermostats only react to certain temperature differences. For example, with some thermostats, the target temperature must be 1°C higher than the room temperature.

<div class="center-table" markdown>
| Target temperature | Room temperature | heating |
| ------------------ | ---------------- | ------- |
| 21°                | 20°              | no      |
| 21°                | 20.5             | no      |
| 21°                | 19.5°            | yes     |

<sup>*Normal behavior without Aggressive Mode*</sup>
</div>

To counteract this, you can deliberately choose the target temperature to be higher or lower to cause heating or closing of the valve. You can dynamically implement this behavior with the *Aggressive Mode*.

``` mermaid
packet-beta
  title Example: Target temperature = 20°, Range = 0.2°, Offset = 2°
  0-13: "Below the range: target temperature + offset"
  14-17: "Range: 19.8°-20.2°"
  18-31: "Above the range: target temperature - offset"
```

## 😡 Aggressive Range

You can set a range around your target temperature within which the actual temperature is set. This means: If the room temperature is within this range, the normal target temperature is set. However, if it is higher or lower, an offset is added.

## ↕ Aggressive Offset

The offset indicates how many degrees are added to make your thermostat start heating. This is then added to the target temperature if the room temperature is outside the range you defined.

!!! info "Remember that the target temperature is modified and no longer corresponds to the actual target temperature."

## 🌡️ Aggressive Calibration

If your thermostat is calibrated natively, i.e., via a special entity, the Aggressive Mode can also be modulated to the calibration. This has the advantage that your thermostat always displays the correct target temperature. However, the locally measured temperature may then differ.