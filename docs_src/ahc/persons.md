---
hide:
  - toc
---
# 👥 Persons

Persons are used as triggers to set the comfort temperature. If one of the defined persons is at home, the comfort temperature is set.
For example, if schedules or presence sensors are also defined, they are evaluated together with the persons in a logic.

!!! warning "An overview explaining the logic will follow later in the documentation."

## 👥 Persons

Here you specify the persons who usually occupy the room to be heated.

## 🏠 Enter Home Duration

Sometimes you just need to be in the apartment briefly without heating. Therefore, a time tolerance can be specified for how long a person must be at home before the heating starts.

## 💨 Leaving Home Duration

Sometimes you just leave the house for a few minutes. To avoid unnecessarily draining the batteries of the thermostats, you can prevent setting the eco temperature by also setting a time tolerance here.

## 🤝 Guest Mode

If you have guests in the house but you are not at home, you can specify a boolean entity here that you can manually trigger. Even if you do not use the person integration, you can specify a boolean entity here that has its own logic to simulate persons being at home.