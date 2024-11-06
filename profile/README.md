# BoilerBeacon - BLE supported Building Notification
`Spring 2023 - Purdue University CNIT 425 Group Project`  
iBeacon based building notification application

## Introduction

Our main motivation is to help people that are visually impaired or blind.
Our project is creating an application that notifies users what building they are entering at Purdue University. 

## Approach

Peripheral Positioning system - FEASYCOM FeasyBeacon Mini using AltBeacon Library

Data Repository - Firebase firestore 

User Interface - Contraint Layout using Listview and implemented Google Maps API


## Outcomes

We designed an app which interacts with FeasyBeacon which using bluetooth. These beacons are placed on doorways of buildings. 
The app on our phone reads the bluetooth signal sent by the beacon and based on that we retrieve building information from firebase.
Text to speech is used to help people navigate around know where they are going. All of this is done as a foreground service so
it runs in the background and notifies the user when they are either approaching/entering/exiting a building


`MainActivity.java` - In handles logic for the all the UI componenets(Fragments, Listview, Contraint Layout), Google Maps API and Firebase connection.
Firebase connection is done through async task and implemented in a way that data is pulled from firebase only when a change is triggered


`ForegroundBeaconService.java` - Handles backend logic for the interacting with beacon and also handles all the necessary configuration for the range and 
notifications.

![Beacon diagram](buildingEntranceFlow_Entering.png)

As we can see in the diagram when we entering the outer radius, approaching command is returned. As enter the inner radius we enter the building
and the building information is returned. The beacon returns us a unique value linked to that specific beacon. In this diagram being 11001. 110 represents the building and 01 represents the door.

![Beacon diagram](buildingEntranceFlow_exiting_edited.png)

We can see a similar logic when the user exits the door. We have 2 status's. We first go back into approaching mode and as soon as we leave the inner radius we are in exiting mode. Our beacon can sense how far we are from the beacon and also if we moving closer or away from beacon which helps us determine what stage we are in.


In order to run the application
1) Fork Repository on local computer
2) Open project using android studio
3) Run on emulator/ local device

## Future plans

Assign an appropriate data (phone numbers) to Audio Guidance button.

Try to reduce current high fluctuation in range detection between Android Device and Beacon.

Consider to implement better UI representation for providing necessary information.


## Demo video

https://youtu.be/iudE-WWK_yQ
