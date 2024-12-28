---
hide:
  - toc
---
# 🏃 Away Mode

The away mode lowers the temperature if comfort is set and you briefly leave the house or room. You have several options for this.

## 🏃 Away Temperature Offset

The offset that is subtracted from the current comfort temperature if the away mode is triggered. *0* means off.

## ⏲️ Schedule Away Mode

If this option is activated, the away mode is activated as soon as the active schedule is *on* but no one is at home. If the schedule is *off* and no one is at home, the eco temperature is set as usual.

## 🚶 Presence Away Mode

If someone is at home but no presence is detected, the away mode is activated.

| Presence        | Person   | Presence Schedule | Mode      |
| --------------- | -------- |------------------ | --------- |
| Detected        | home     | not set           | Comfort   |
| Not Detected    | home     | not set           | Away Mode |
| -               | not home | no matter         | Eco       |
| Detected        | home     | on                | Comfort   |
| Not Detected    | home     | on                | Away Mode |
| Detected        | home     | off               | Eco       |
| Not Detected    | home     | off               | Eco       |


## 🚶 Ignore People For Presence Away Mode

If you want to ignore persons for the away mode enable this option.

| Presence        | Presence Schedule | Mode      |
| --------------- |------------------ | --------- |
| Detected        | not set           | Comfort   |
| Not Detected    | not set           | Eco       |
| Detected        | on                | Comfort   |
| Not Detected    | on                | Away Mode |
| Detected        | off               | Eco       |
| Not Detected    | off               | Eco       |