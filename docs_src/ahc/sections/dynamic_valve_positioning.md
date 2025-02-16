---
hide:
  - toc
---
# ⌖ Dynamic Valve Positioning

Usually, the valves of your thermostats are always 100% open, except the target temperature is reached. To prevent your thermostat from behaving like a relay, i.e., only opening and closing, you can dynamically influence the valve position here.

!!! info "Your thermostat must support this and the respective integration must provide an entity for the valve opening."

## ⌖ Valve Positioning Mode

The positioning mode determines when and how much the valve is closed or opened. This depends on your rooms, the heating surface, the flow temperature, etc.

<table>
  <colgroup>
    <col span="1" style="width: 33%;">
    <col span="1" style="width: 33%;">
    <col span="1" style="width: 33%;">
  </colgroup>
  <tr>
    <th>Regular</th>
    <th>Optimisitc</th>
    <th>Pessimistic</th>
  </tr>
  <tr>
    <td>This is the default setting and should be chosen if the radiators and flow temperature are ideally matched to your room.</td>
    <td>Here the valve closes faster at the beginning because your radiators still have enough heat to heat the room or the flow temperature for the said room is set too high.</td>
    <td>Here the valve closes faster at the beginning because your radiators still have enough heat to heat the room or the flow temperature for the said room is set too high.</td>
  </tr>
  <tr>
    <td>  
      ``` mermaid
      ---
      config:
        themeVariables:
          xyChart:
            plotColorPalette: "#e52000"
            xAxisTitleColor: "#e52000"
      ---
      xychart-beta
        title "Regular"
        x-axis "Temperature (in °C)" 15 --> 20
        y-axis "Valve Opening (in %)" 0 --> 100
        line [100, 100, 100, 87.5, 75, 62.5, 50, 37.5, 25, 12.5, 0]
      ```
    </td>
    <td>
      ``` mermaid
      ---
      config:
        themeVariables:
          xyChart:
            plotColorPalette: "#e52000"
            xAxisTitleColor: "#e52000"
      ---
      xychart-beta
        title "Optimistic"
        x-axis "Temperature (in °C)" 15 --> 20
        y-axis "Valve Opening (in %)" 0 --> 100
        line [100, 100, 100, 76, 56, 39, 25, 14, 6, 1.5, 0]
      ```
    </td>
    <td>
      ``` mermaid
      ---
      config:
        themeVariables:
          xyChart:
            plotColorPalette: "#e52000"
            xAxisTitleColor: "#e52000"
      ---
      xychart-beta
        title "Pessimistic"
        x-axis "Temperature (in °C)" 15 --> 20
        y-axis "Valve Opening (in %)" 0 --> 100
        line [100, 100, 100, 93.5, 86.6, 79.05, 70.71, 61.24, 50, 35.5, 0]
      ```
    </td>
  </tr>
</table>

## ↔️ Positioning Temperature Difference

Here you can specify when the automation should modulate the valve opening depending on your target temperature.
In the graphs shown above, the target temperature is 20°. Modulation starts at 16°. So, a *Positioning Temperature Difference* of 4° is set here.

## 🦶 Valve Positioning Step Size

The *Step Size* indicates the steps in which modulation occurs. The smaller the value, the more precise but also more frequent the valve position adjustment. You can choose from *5%*, *10%*, or *20%*.

## ⏱️ Valve Positioning Timeout

If you have strong temperature fluctuations or have set a small *Step Size*, you can reduce the frequency of adjustments by setting a timeout here that must elapse between two adjustments before the automation adjusts the valve position again.

## 🗝️ Positioning Entity Keyword

Your thermostat must support valve positioning. If this is the case, you can find the respective entity in the overview of your thermostat.
Open the settings for the entity and look at the Entity ID. The keyword must partially match the Entity ID.

| Possible Entity ID                                   | Suggested Keyword             |
| ---------------------------------------------------- | ----------------------------- |
| number.room_thermostat_links_valve_opening_degree    | valve_opening_degree          |