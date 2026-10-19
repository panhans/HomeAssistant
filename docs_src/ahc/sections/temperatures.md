---
hide:
  - toc
---
# 🌡️ Temperatures

## 🛋️ Static Comfort Temperature

The comfort temperature is the temperature that is set when you might be at home or your presence sensor is triggered or your heating schedule is *on*.
This temperature setting serves as a fallback temperature. If a static temperature is sufficient for you and you do not want to adjust it further via the UI, this setting is sufficient.
However, temporal temperature adjustments can be made via the adjustments.

## 🌱 Static Eco Temperature

The eco temperature is the temperature that is set when you are not at home, for example, or your schedule does not prescribe heating to the comfort temperature.
This temperature setting serves as a fallback temperature. If a static temperature is sufficient for you and you do not want to adjust it further via the UI, this setting is sufficient.
However, temporal temperature adjustments can be made via the adjustments.

## 🛋️ Comfort Temperature

If you want to control the comfort temperature via the UI, you can specify an `input_number` helper here. This overrides the static comfort temperature.

A `number` or a temperature `sensor` works too, for example the comfort temperature that a thermostat or a heating controller already provides, so no helper is needed. If the entity is `unavailable` or `unknown`, the fallback temperature is used.

## 🌱 Eco Temperature

If you want to control the eco temperature via the UI, you can specify an `input_number` helper here. This overrides the static eco temperature.

A `number` or a temperature `sensor` works too, see the comfort temperature.

!!! info "NOTE"

    The automation only reads these entities, except for the *physical change* / *UI change* sync and the heating schedule adjustments. They write the changed temperature into the entity, which works for `input_number` and `number` entities. A `sensor` is never written. Keep that in mind before you point the sync at a `number` that is stored in a device.
