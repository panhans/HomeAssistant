---
hide:
  - toc
---
# 🕑 Scheduling

Mit Schedules kannst du einen einfachen Heizplan erstellen mit dem du zwischen der Eco und der Comfort Temperatur wechseln kannst. Weiterhin kannst du mit den Heating Adjustments und auch mit Personen Einfluss auf das Verhalten und auf die Temperaturen nehmen.

!!! warning "An overview explaining the logic will follow later in the documentation."

## 🕑 Schedules

Here you can add your schedules. Schedules are helpers that you can easily create in your Home Assistant.

<figure markdown="span">
  ![Image title](images/ahc/heating_scheduler.png){ width="300" }
  <figcaption>Example Heating Schedule - Blue means comfort mode</figcaption>
</figure>

You can set as many schedules as you like. To select a schedule, you can do it by providing a Schedule Selector.

## 👆 Schedule Selector

Here you can specify an entity that determines the selection of the active schedule. If you only have one schedule, you can ignore this point.
If you want to switch between two schedules, a binary entity is sufficient. However, you can also specify entities whose status is a number, thus activating the respective scheduler. Entities that hold text as status are also possible. The value is then matched with the friendly name of the respective schedule. It only needs to partially match.

| Type            | Possible Values           | Example            | Description                                                                          |
| --------------- | ------------------------- | ------------------ | ------------------------------------------------------------------------------------ |
| binary_sensor   | on, off                   | *on*               | Selects the 2nd of max two schedules                                                 |
| input_boolean   | on, off                   | *off*              | Selects the 1st of max two schedules                                                 |  
| input_text      | *custom text*, *integers* | *Holiday*          | Selects the first schedule that contains the word *Holiday* in its friendly name     |
| input_number    | *integers*                | *3*                | Selects the 3rd schedule                                                             |
| input_select    | *custom text*, *integers* | *Workday Schedule* | Selects the first schedule that contains the *Workday Schedule* in its friendly name |