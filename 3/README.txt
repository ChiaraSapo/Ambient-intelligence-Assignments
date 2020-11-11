CLASSES (not all subclasses are shown):
They are all disjoint
- APP
   - app alert: notification a person receives when isExpensive is set.
   - app signal: message to send from app to turn heat on.
- Day
- Floor
- Object
- Person
- Room
- Season


OBJECT PROPERTIES:
To describe a person/object in a room:
- hasIn
- isIn
To describe a room on a floor:
- hasOn
- isOn
To describe an app alarm received by a person:
- hasReceived
- isReceived
To describe an app message sent from a person:
- isSend
- isSent


DATA PROPERTIES:
To describe quantitatively the temperature of a room, floor, boiler or to define the desired temperature from app:
- hasTemperature
To describe a person arriving home (range: decimals intended to measure minutes: 0.10 equals 10minutes):
- isComingHomeIn
To describe time of the day (range: the same as before)
- isTime
To describe the fact that a boiler is consuming too much (threshold is asssumed to be predefined by the user on the app):
- isTooExpensive


SWRL RULES:
- ReceiveAppAlarm: to use it set Boiler1 data properties isExpensive to a number higher than 10. All Person individuals will have data property hasReceive set.
SetBoilerTempComingHome: to use it set a Person individual data property isCoimingHomeIn to a value lower than 0.30. Boiler1 data property hasTemperature will be set to a standard value.
- SetBoilerTemperatureFF: to use it set Today data property isTime to a value v>20,v<8. The other rule inputs are already set.
- SetBoilerTemperatureGF: to use it set Today data property isTime to a value 8<v<20. The other rule inputs are already set.
- SignalFromApp: to use it set a Person individual object propery to isSend AppSignal1 and set AppSignal1 data property to a desired temperature (or just leave the current value). Boiler1 data property hasTemperature will be set to that temperature.
