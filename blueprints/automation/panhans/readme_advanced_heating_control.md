# :fire: **ADVANCED HEATING CONTROL <sup>v3</sup>** :fire:

## Minimal configuration

For a minimal configuration setup your valves and your prefered temperature. That means the *comfort temperature* and the *minimum temperature*.<br/>
The *comfort temperature* will be set if the conditions you can setup match. Otherwise the *minimum temperature* will be set.

## Heating Possibilites

Now you are ready to go to setup some conditions. There are three different approaches to setup your intelligent heating plan. And all can be combined together to make it flexible like you want.

### 1. Heating based on persons who are at home

You can configure your heating automation simply by persons who are at home. If you use the companion app it's easy to track this.<br/>
So just define at least one person for the automation. This should be the person who's living in the room.<br/>
<br/>
Now your automation works person based. If the person is home *comfort temperature* will be set.

### 2. Scheduler based heating

You can define schedulers in home assistants helper section. The schedulers works like plans for your heating.<br/>
You also can setup a 2nd scheduler for holidays which can be switched by an *input_boolean* or a boolean sensor.<br/>

#### Fully timebased
If you want to use it fully timebased. Leave the person section empty.

#### Combined with persons
Setup some persons. So now *comfort temoerature* will be set if the scheduler is *on* and somebody is home.<br/>
Let's say you heat the during the day and leave your home heating will be set to *minimum temperature*.

### 3. Presence based heating
You can setup a presence detector. If you leave persons and the schedulers empty the automation works fully presence based.<br/>
If presence is detected the *comfort temperature* will be set.<br/>
There is an option to couple it with persons. So the presence detection is just enabled if somebody is home.<br/>
If you want you can also define time windows where presence detection shall be active. For that purpose you can define another scheduler for presence detection.

# Example Configuration
Let's say I am the only one whos living in a room. So I setup the automation and define me as person.<br/>
I want the room to be heated from 9.00 - 20.00 o'clock. Let's define a scheduler for that room.<br/>
<br/>
Now my automation set the thermostats to *comfort temperature* if the scheduler is *on* and I am *home*.<br/>
<br/>
But wait. Heating is only configured till 20.00 o'clock. There are some days I stay awake and do some work or watching TV but I don't want to heat stupidly to 24:00 o'lock.<br/>
Let's add a presence sensor for it. I know, if I am in that room in the evening I always have my lights on. So I take my grouped lights or at least one light and create an fake presence sensor.<br/>

Lets put this sensor to my configuration. Now I want the automation that the sensor only come in the game after 20:00 o'clock.<br/>
I need another scheduler to define the time window when the presence detection shall be avtive.<br/>
<br/>
This configuration makes heating up the room from 9.00 - 20.00 o'clock if I am home. And after 20.00 o'clock if I am in the room. If I turn off my lights heating will also turned down.

# Combination Overview

|                   | Person                                                                                                               | Heating Scheduler<sup>1</sup>                                                                                           | Presence Sensor<sup>2</sup>                                                                                                     |
|-------------------|----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Person**            | :fire: somebody is home<br/> :snowflake: nobody is home                                                              | :fire: scheduler is on **and** somebody is home<br/> :snowflake: scheduler is off **or** nobody is home     | :fire: somebody is home **and** presence is detected</br> :snowflake: nobody is home **or** no presence is detected  |
| **Heating Scheduler<sup>1</sup>** | :fire: scheduler is on **and** somebody is home <br/> :snowflake: scheduler is off **or** nobody is home             | :fire: scheduler is on <br/> :snowflake: scheduler is off                                                   | :fire: scheduler is on **or** presence is detected<br/> :snowflake: scheduler is off **and** no presence is detected |
| **Presence Sensor<sup>2</sup>**   | :fire: presence is detected **and** somebody is home<br/> :snowflake: no presence is detected **or** nobody is home  | :fire: scheduler is on **or** presence is detected<br/> :snowflake: scheduler is off **and** nobody is home | :fire: presence is detected<br/> :snowflake: no presence is detected                                                 |

> **1**: You can choose between two heating schedulers a main one and a *holiday scheduler*. You can switch between them by providing your *holiday sensor / toggle*.

> **2**: You can set time windows when presence detection shall be enabled by providing a *presence detection scheduler*.