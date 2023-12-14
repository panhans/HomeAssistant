# :fire: **ADVANCED HEATING CONTROL <sup>v3</sup>** :fire:

# Table of Contents
1. [Base configuration](#1-Base-configuration)
2. [Heating Possibilites](#2-Heating-Possibilites)<br/>
  2.2 [Scheduler based heating](#22-Scheduler-based-heating)<br/>
    2.2.1 [Fully time/scheduler based](#221-Fully-timescheduler-based)<br/>
    2.2.2 [Scheduler combined with persons](#222-Scheduler-combined-with-persons)<br/>
  2.3 [Presence based heating](#23-Presence-based-heating) <br/>
  2.3.1 [Fully presence based](#231-Fully-presence-based)<br/>
  2.3.2 [Presence combined with persons](#232-Presence-combined-with-persons)
3. [Combination Overview](#3-Combination-Overview)
4. [Example Configuration](#4-Example-Configuration)




## 1. Base configuration

For a minimal configuration setup your valves and your prefered temperature. That means the *comfort temperature* and the *minimum temperature*.

![Valves](images/valves.png "Valves")

The *comfort temperature* will be set if the conditions you can set up match. Otherwise the *minimum temperature* will be set.


![Temperatures](images/temps.png "Temperatures")

>**Note**: with this configuration, heating is not possible. It's just a base setup.<br/>
For some features, you need to provide a comfort temperature *input_number* entity.

## 2. Heating Possibilities

Now you are ready to go to set up more entities that make use of your base setup.<br/>
There are three different approaches to setup your intelligent heating plan and all can be combined to make it as flexible as you want.

### 2.1 Heating based on persons who are at home

You can configure your heating automation simply by persons who are at home. If you use the companion app it's easy to track persons devices (Android Phones / iPhones) or just map a network device to a certain person.<br/>
So just define at least one person for the automation. This should be the person who's living in the room.<br/>

![Persons](images/persons.png "Persons")

Now your automation works person based. If the person is home *comfort temperature* will be set.

### 2.2 Scheduler-based heating

You can define schedulers in home assistants helper section. 

[![Open your Home Assistant instance and show your helper entities.](https://my.home-assistant.io/badges/helpers.svg)](https://my.home-assistant.io/redirect/helpers/)

The schedulers work like plans for your heating. 

![Scheduler](images/scheduler.png "Scheduler")

You also can set up a 2nd scheduler for holidays which can be switched by an *input_boolean* or a *boolean sensor*.

![Holiday](images/holiday.png "Holiday")

#### 2.2.1 Fully time/scheduler based
If you want to use it fully time based just leave the person section empty.

#### 2.2.2 Scheduler combined with persons
Set up some persons. So now *comfort temperature* will be set if the scheduler is *on* and somebody is home.<br/>

> You can setup a guest mode entity (*input_boolean, binary_sensor*) that simulates a person. Good when someone is sitting your kids / pets / house and nobody of the residents are home.

### 2.3 Presence-based heating

You can set up a *presence detector*. This means if *presence detected* then *heat* to *comfort temperature*.

#### 2.3.1 Fully presence based
If you leave persons and the schedulers empty the automation works fully presence based.<br/>
If presence is detected the *comfort temperature* will be set.

#### 2.3.2 Presence combined with persons
If you set up some persons it is coupled with them. So the presence detection is just enabled if somebody is home.<br/>
If you want you can also define time windows where presence detection shall be active. For that purpose, you can define another scheduler for presence detection.

# 3. Combination Overview

|                   | Person                                                                                                               | Heating Scheduler<sup>1</sup>                                                                                           | Presence Sensor<sup>2</sup>                                                                                                     |
|-------------------|----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Person**            | :fire: somebody is home<br/> :snowflake: nobody is home                                                              | :fire: scheduler is on **and** somebody is home<br/> :snowflake: scheduler is off **or** nobody is home     | :fire: somebody is home **and** presence is detected</br> :snowflake: nobody is home **or** no presence is detected  |
| **Heating Scheduler<sup>1</sup>** | :fire: scheduler is on **and** somebody is home <br/> :snowflake: scheduler is off **or** nobody is home             | :fire: scheduler is on <br/> :snowflake: scheduler is off                                                   | :fire: scheduler is on **or** presence is detected<br/> :snowflake: scheduler is off **and** no presence is detected |
| **Presence Sensor<sup>2</sup>**   | :fire: presence is detected **and** somebody is home<br/> :snowflake: no presence is detected **or** nobody is home  | :fire: scheduler is on **or** presence is detected<br/> :snowflake: scheduler is off **and** nobody is home | :fire: presence is detected<br/> :snowflake: no presence is detected                                                 |

> **1**: You can choose between two heating schedulers a main one and a *holiday scheduler*. You can switch between them by providing your *holiday sensor / toggle*.

> **2**: You can set time windows when presence detection shall be enabled by providing a *presence detection scheduler*.

# 4. Example Configuration
Let's say I am the only one who's living in a specific room. So I set up the automation and defined myself as person.<br/>

![Persons](images/persons.png "Persons")

I want the room to be heated in the morning and afternoon and the whole day on weekends. Let's define a scheduler for that room.

<img src="images/heating_scheduler.png" width="300"/>

Now my automation sets the thermostats to *comfort temperature* if the scheduler is *on* and I am *home*. Nice!<br/>
<br/>
But wait: Heating is only configured till 4 pm. There are some days I stay awake and do some work or watch TV but I don't want to heat stupidly to 12 pm o'clock.<br/>
Let's add a presence sensor for this case. I know, if I am in that room I always have my lights on in the evening. So I take my grouped lights or at least one light and create a fake presence sensor, a template-based sensor in the helper section.<br/>

<img src="images/presence_sensor.png" width="300"/>

Let's put this sensor into my configuration.

![Presence setup](images/presence.png "Presence setup")

Now I want the presence sensor only to get in the game after 4 pm.<br/>
I need another scheduler to define the time window when the presence detection shall be active.

<img src="images/presence_scheduler.png" width="300"/>

Let's put the scheduler in our configuration.

![Presence scheduler](images/presence_with_scheduler.png "Presence scheduler")

This configuration makes heating the room from 7 am - 4 pm if I am home. And after 4 pm if I am in the room based on presence. If I turn it off, my heating will also be turned down.
