---
hide:
  - toc
---
# 🤜 Force Comfort / Eco Mode

## 🎈 Party Mode

The party mode activates the comfort mode and thus overrides schedules or presence sensors. Here you can use binary entities or timers.
If you append a number to the end of the friendly name, it will be interpreted as a temperature and set accordingly.
When the windows are opened, the thermostats are still turned off or down.

| Type             | Example             | 
| --------------- | ------------------- |
| binary_sensor   | binary_sensor.party |
| input_boolean   | input_boolean.party |
| timer           | timer.party         |

!!! info "NOTE"

    If you name your entity like *Party Mode 25* the target temperature is set to 25° if the entity is enabled / running.

## 🥵 Force Max Temperature

Force Max temperature sets all thermostats to their maximum. Even if the windows are open, the thermostats remain at the highest level.
This function is to be used, for example, during the maintenance of the central heating system.

## 🌱 Force Eco Temperature

This setting suppresses the comfort mode and sets the eco mode. The window detection still works.

## 🔄 Legacy Restore

The restoration of temperatures is realized through temporary scenes. Some thermostats have problems with this method and do not return to the previous setting.
In this case this option can be activated. The temperature is determined by the automation but may differ from the previous one if the thermostat was manually adjusted.