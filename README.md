# This repo explains my HomeAssistant configuration

## Background

If you aren't already familiar with HomeAssistant (HASS), please start here: [Home Assistant - Getting Started](https://www.home-assistant.io/installation/)

I use HASS to automate interactions between the following:

- my solar array (SolarEdge)
- my home battery (Tesla Powerwall)
- my EV charger (MyEnergi Zappi)
- my car (Audi E-tron)
- my electrictiy provider (Octopus, using the Intelligent Octopus Go tariff)

---

## HASS integrations

I use the following integrations

| Integration              | Link                                                         |   Type   | What I use it for                                                                                                                                                                                                            |
|--------------------------|--------------------------------------------------------------|:--------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Audi Connect             | https://github.com/audiconnect/audi_connect_ha               |   HACS   | connecting to my car's API                                                                                                                                                                                                   |
| Tesla Custom Integration | http://homeassistant.local:8123/hacs/repository/362700564    |   HACS   | Sending commands to my Powerwall to stop it discharging                                                                                                                                                                      |
| Tesla Powerwall          | https://www.home-assistant.io/integrations/powerwall         | Official | this provides a local connection to your Powerwall rather than through Tesla's servers. Faster if you just want to read the PW's state, but doesn't allow you to set the PW's reserve.                                      |
| SolarEdge                | https://www.home-assistant.io/integrations/solaredge         | Official | I don't use this in automations, as I get solar data from the Powerwall integration.  You may need this,  or the equivalent for your solar array, if your battery or EV charger doesn't monitor the amount of solar produced |
| Local Calendar           | https://www.home-assistant.io/integrations/local_calendar    | Official | I use a calendar for Octopus to track savings sessions  and run automations for them                                                                                                                                         |
| myenergi                 | https://github.com/cjne/ha-myenergi                          |   HACS   | to automate my EV chargers                                                                                                                                                                                                   |
| Octopus Energy           | https://bottlecapdave.github.io/HomeAssistant-OctopusEnergy/ |   HACS   | to find out about off-peak periods, free periods and saving sessions                                                                                                                                                         |

---

## automations.yaml

You can find each of the following automations in the automations.yaml file.  
Some of the integrations use device IDs and it's probably simpler to add these via the UI rather than copy/pasting my yaml config and trying to work our which device IDs to use in your HASS installation.  I've provided screenshots of the UI for these under the screenshots folder.
In some places, you will need to replace placeholder values for entities with the specific values for your installation, there is a list of these below, as well as in the yaml file.


### List of automations



---

## configuration.yaml

I have split my configuation file into separate files for automations, scripts, sensors (see: [Splitting Up The Configuration](https://www.home-assistant.io/docs/configuration/splitting_configuration/))
You will need to copy the content of my configuration file.  You may have other content in your configuration file already.  If so, add my content to the beginning rather than overwriting what you aleady have.

---
## sensors.yaml

This file shows a specific sensor I have to help me automatically set-up the amount of charge I want from Octopus each night.  
My 'real' sensors.yaml file contains a lot of other sensors to drive different dashboards.  I have removed these for clarity.

---

## scripts.yaml

This file contains two scripts to control my car.  This is specific to the Audi integration and may work differenly for your EV.
I have made these car commands into scripts to allow me to keep my car's VIN private rather than posting it into Github.
You could choose to just put the commands directly into the automation that needs them rather than keeping them as scripts.  
If you keep the scripts, you will need to either:

a) change '!secret audi_vin' to just be your car's VIN (which you can find in your MyAudi app, or by logging into myaudiconnect.com), or
b) add a secrets.yaml file and include the line 
    `audi_vin: WAUxxxxxxxxxxxxxx` where WAUxxxxxxxxxxxxxx is your car's actual VIN number, which is a 17-digit code starting with WAU
    
---

## substitutions you will need to make to the files

You will find that some of the HASS entities you need to use will be named specifically for your installation.  Wherever you see something in square brackets in the yaml files, you'll need to fine the correct value to replace this with for your installation.
I have listed the substutions below.  Each of the yaml files also contains this information.





