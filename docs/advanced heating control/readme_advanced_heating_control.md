# :fire: **ADVANCED HEATING CONTROL <sup>v3</sup>** :fire:

## Base configuration

For a minimal configuration setup your valves and your prefered temperature. That means the *comfort temperature* and the *minimum temperature*.

![Valves](images/valves.png "Valves")

The *comfort temperature* will be set if the conditions you can setup match. Otherwise the *minimum temperature* will be set.


![Temperatures](images/temps.png "Temperatures")

>**Note**: with this configuration heating is not possible. It's just a base setup.<br/>
For some features you need to provide a comfort temoperature *input_number* entity. Also if you want to change it in your front end.

## Heating Possibilites

Now you are ready to go to setup your entities that make use of your base setup.<br/>
There are three different approaches to setup your intelligent heating plan and all can be combined together to make it flexible like you want.

### 1. Heating based on persons who are at home

You can configure your heating automation simply by persons who are at home. If you use the companion app it's easy to track this or just map a networkdevice to a certain person.<br/>
So just define at least one person for the automation. This should be the person who's living in the room.<br/>

![Persons](images/persons.png "Persons")

Now your automation works person based. If the person is home *comfort temperature* will be set.

### 2. Scheduler based heating

You can define schedulers in home assistants helper section. 

[![Open your Home Assistant instance and show your helper entities.](https://my.home-assistant.io/badges/helpers.svg)](https://my.home-assistant.io/redirect/helpers/)

The schedulers works like plans for your heating. 

![Scheduler](images/scheduler.png "Scheduler")

You also can setup a 2nd scheduler for holidays which can be switched by an *input_boolean* or a boolean sensor.

![Holiday](images/holiday.png "Holiday")

#### 2.1 Fully time/scheduler based
If you want to use it fully timebased. Leave the person section empty.

#### 2.2 Scheduler combined with persons
Setup some persons. So now *comfort temoerature* will be set if the scheduler is *on* and somebody is home.<br/>
Let's say you heat the during the day and leave your home heating will be set to *minimum temperature*.

### 3. Presence based heating

You can setup a *presence detector*. Which means *presence detected* then *heat* to *comfort temperature*.

#### 3.1 Fully presence based
If you leave persons and the schedulers empty the automation works fully presence based.<br/>
If presence is detected the *comfort temperature* will be set.

#### 3.2 Presence combined with persons
There is an option to couple it with persons. So the presence detection is just enabled if somebody is home.<br/>
If you want you can also define time windows where presence detection shall be active. For that purpose you can define another scheduler for presence detection.

# Combination Overview

|                   | Person                                                                                                               | Heating Scheduler<sup>1</sup>                                                                                           | Presence Sensor<sup>2</sup>                                                                                                     |
|-------------------|----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Person**            | :fire: somebody is home<br/> :snowflake: nobody is home                                                              | :fire: scheduler is on **and** somebody is home<br/> :snowflake: scheduler is off **or** nobody is home     | :fire: somebody is home **and** presence is detected</br> :snowflake: nobody is home **or** no presence is detected  |
| **Heating Scheduler<sup>1</sup>** | :fire: scheduler is on **and** somebody is home <br/> :snowflake: scheduler is off **or** nobody is home             | :fire: scheduler is on <br/> :snowflake: scheduler is off                                                   | :fire: scheduler is on **or** presence is detected<br/> :snowflake: scheduler is off **and** no presence is detected |
| **Presence Sensor<sup>2</sup>**   | :fire: presence is detected **and** somebody is home<br/> :snowflake: no presence is detected **or** nobody is home  | :fire: scheduler is on **or** presence is detected<br/> :snowflake: scheduler is off **and** nobody is home | :fire: presence is detected<br/> :snowflake: no presence is detected                                                 |

> **1**: You can choose between two heating schedulers a main one and a *holiday scheduler*. You can switch between them by providing your *holiday sensor / toggle*.

> **2**: You can set time windows when presence detection shall be enabled by providing a *presence detection scheduler*.

# Example Configuration
Let's say I am the only one who's living in a specific room. So I setup the automation and define me as person.<br/>

![Persons](images/persons.png "Persons")

I want the room to be heated in the morning and afternoon and the hole day on weekend. Let's define a scheduler for that room.

<img src="images/heating_scheduler.png" width="300"/>

Now my automation set the thermostats to *comfort temperature* if the scheduler is *on* and I am *home*. Nice!<br/>
<br/>
But wait: Heating is only configured till 16.00 o'clock. There are some days I stay awake and do some work or watching TV but I don't want to heat stupidly to 24:00 o'lock.<br/>
Let's add a presence sensor for this case. I know, if I am in that room I always have my lights on in the evening. So I take my grouped lights or at least one light and create an fake presence sensor, a template based senso in the helper section.<br/>

<img src="images/presence_sensor.png" width="300"/>

Lets put this sensor to my configuration.

![Presence setup](images/presence.png "Presence setup")

Now I want the presence sensor only get in the game after 16:00 o'clock.<br/>
I need another scheduler to define the time window when the presence detection shall be avtive.

<img src="images/presence_scheduler.png" width="300"/>

Let's put the scheduler to our configuration.

![Presence scheduler](images/presence_with_scheduler.png "Presence scheduler")

This configuration makes heating up the room from 7.00 - 16.00 o'clock if I am home. And after 16.00 o'clock if I am in the room based on presence. If I turn off my lights heating will also turned down.