*** STEP 1 ***

Imagine an Ambient Intelligence application complying with all the requirements described in the slides "Ambient Intelligence - An Introduction", as well as with what you have learns about "Sensors in Ambient Intelligence".

Your application needs to

- focus on environmental intelligence, rather than on "robots". No robots allowed in this exercise.
- focus on people, and how they can interact with the environment and/or take benefit from it
- include sensors.

Feel free to be very creative: you can invent anything you want, given that it complies with requirements grande sorriso

Prepare 2-3 slides (no more) to describe your idea. Do not tell anyone about your idea before the presentation, as you will be requested to present it in front of everybody in 3 minutes!

*** STEP 2 ***

As a second step, you will be required to design an Ontology describing the Ambient Intelligence application that you have proposed. I suggest to read the Pizza Ontology Tutorial, if you didn't do that yet.

Please notice that the Ontology should be "rich" enough in order to describe everything which is relevant in your application, in such a way that - by reading the Ontology - an external reader may understand which are the most relevant concepts and their relationships in your application.

For instance, when describing a house, the relevant concepts might be rooms (and different kind of rooms), furniture (different type of furniture), objects (different types of objects), activities (different kind of activities). Next, you may wish to explain through the Ontology that rooms can be connected to other rooms; rooms can contain furniture and objects; furniture can have
objects inside, upon or below them; actitivies can be performed in rooms (and some of them can be performed only within some specific rooms). This would be the TBox of the Ontology, i.e. describing classes and properties holding between classes.

After this, you could decide to describe a specific house, i.e., by introducing individuals, and the relationships holding between individuals (e.g., in a house there may be two bathrooms, some rooms can be connected to other rooms, and it may contain a specific kind of object in a specific room). This would be the ABox of the Ontology, i.e., containing individual assertions and property assertions.

As already said, please try to be as much rich as you can to describe your application. There is not only a way to do that: think about the solution that is more appropriate in your view.

As a thumb rule:

- At list 3 top Classes are required in the TBox (i.e., immediately below Thing)

- At list 4 Object Properties and 4 Data Properties should be created and used in the TBox

- At list 6 Individual Assertions and 6 Property Assertions should be added in the ABox


MY EXAMPLE:

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