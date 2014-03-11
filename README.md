Monitor
=======

This application demonstrates some features of Windows Store Apps, SignalR hubs, Windows WCF Services, OWIN and Nancy.

# Overview
This is an application demonstrating consuming Signalr hub broadcasts in a Windows Store App. The premise is that you want to monitor important “events” from other applications. The events can be arbitrary in structure as long as the messages prescribe to the format expected. Events are a high level concept in this demo. An event can be a sale on an e-commerce site, an error, somebody logging in somewhere, etc.  


Components
--------------------
#### Monitor.Architecture  
This project is just a test drive of Visual Studio Modeling Projects which shows off some code generation from UML. This project was used to generate the interfaces in Monitor.Core  

#### Monitor.Core
Mainly class implementations of domain objects shared by other components

#### Monitor.Hub
This is a WCF Workflow service that serves the purpose of being the central messaging hub, where applications can broadcast messages by using a service reference to the workflow. This was included because it could be used to serve as a hook for certain types of messaged where additional workflows could be used to perform some process.

#### Monitor.Website
This is a website project utilizing OWIN and Nancy that serves to demonstrate an application (in this case a website) that wishes to broadcast messages. It is a simple one page site that allows a user to broadcast messages. The main purpose was to facilitate showing a real time working monitoring system in the Windows Store App.

#### Monitor.Store

This is the Windows Store App that demonstrates a client listening for broadcasts on a SignalR hub. The application makes use of [ModernUI charts](http://modernuicharts.codeplex.com) by *Torsten Mandelkow* (Nice JOB!), to display a doughnut chart that shows counts of broadcasts by category and title. Each category gets its own Group control.


Quickstart
---
The easiest way to get going with this project is as follows:  

1. Select the Monitor.Store, where you have the choice to run the store app as localmachine vs simulator, choose simulator (so you can interact with the broadcaster website in another window).  
2. Right Click the solution, go to Properties, Startup Project, and select multiple startup projects. Set Monitor.Hub, Monitor.Store, and Monitor.Website as startup projects. Run the solution.  
3. . In the browsers running Monitor.Website, you can select a message category, add a message title, and content (all required). You should see a group control representing your broadcast. For each unique category you broadcast, a new group control will appear, furthermore, to increment the count of each type of message, give it the same title, each unique title will become another item on the group chart representing the category. You can double click the group control to go to the Split Page Items View where you can see the timestamp and content of each individual message in the respective category.

**YOU MUST HAVE AN INSTANCE OF THE Monitor.Hub application RUNNING**, or there will be no hub to receive and broadcast messages, and the store app will be a blank screen with a label.




