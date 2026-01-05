# 🔥 Advanced Heating Control

## 🔴 Version 5.5.0

- input number for window open temperature
- fallback option (off/heat) if weather entity or ouside temperature get unavailable or unknown
- persons could be replaced by device trackers (recommended)
- minimal configuration revised (window detection, liming protection)
- event based restore after liming protection
- static temperatures renamed to fallback temperatures
- fallback temperature (static temperatures) could be replaced by input number entities
- revised sections, selectors, and descriptions
- idle temperature when automation is turned off (winter mode off)
- dedicated hvac actions for eco mode and comfort mode
- new logic for physical or ui / thermostat cards changes
- summarized calibration logic:
    - calibration on/off toggle
    - automatic detection of offset or external temperature source for calibration
    - thermostats with external calibration get keep alives every 10 min automatically
  <br/><br/>  

### 💥 BREAKING CHANGES
- *off instead of eco* has been removed (set hvac mode *off* in eco mode options)
- *physical changed* is independent from ui changed now. check your settings if you need
