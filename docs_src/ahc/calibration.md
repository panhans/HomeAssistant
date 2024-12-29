---
hide:
  - toc
---
# 🧭 Calibration

If you have specified a room thermometer and your thermostats support native calibration, it is automatically active. Here you can fine-tune the calibration.

## ⏳ Calibration Timeout

To prevent your calibration from being triggered too frequently, you can set a timeout here. This time is a minimum interval between two calibration calls.

!!! info "This setting does not apply to Danfoss, Popp & Hive thermostats, as they need to be triggered more frequently to prevent the calibration value from being lost."

## ↔️ Calibration Delta

To prevent calibration from being triggered by the slightest temperature change, you can specify a minimum distance here that must lie between the old calibration value and the new one for the calibration to be triggered.

### Example

| Room Temperature | Thermostat Temperature | Difference | Calibration Delta | Calibration |
| ---------------- | ---------------------- | ---------- | ----------------- | ----------- |
| 20°              | 20.5°                  | 0.5°       | 1°                | No          |
| 20°              | 21°                    | 1°         | 1°                | Yes         |

## 🗝️ Calibration Entity Key Word

Your thermostat usually has an entity for calibration. You can find this in the device overview in Home Assistant. All entities are named according to a specific schema. To ensure the automation selects the correct entity, you must specify the correct keyword here.

### Example

| Possible Entity ID                                   | Suggested Keyword             |
| ---------------------------------------------------- | ----------------------------- |
| number.room_thermostat_local_temperature_calibration | local_temperature_calibration |
| number.room_thermostat_external_calibration          | external_calibration          |
| number.room_thermostat_temperature_offset            | offset                        |


## 🦶 Step Size

Usually, the step size, i.e., the minimum adjustment of your calibration entities, is automatically determined. However, there are exceptions where the entity only accepts whole or smaller values than specified. Here you can override the automatic detection. Please pay attention to the Home Assistant log if this causes errors.

## 🧭 Generic Calibration

If your thermostat does not support native calibration, you can enable Generic Calibration. In this case, the offset is added to the target temperature of your thermostat.

!!! info "Your thermostat will no longer display the actual temperature but a corrected one."

| Room Temperature | Thermostat Temperature | Difference | Target Temperature | Calibrated Target Temperature |
| ---------------- | ---------------------- | ---------- | ------------------ | ----------------------------- |
| 20°              | 22°                    | 2°         | 20°                | 22°                           |
| 22°              | 20°                    | 2°         | 20°                | 18°                           |

## ↕️ Generic Calibration Offset

If the calculated offset is too high for you, you can limit it with this option.