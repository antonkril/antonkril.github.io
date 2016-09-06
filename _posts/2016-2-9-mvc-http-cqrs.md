---
layout: post
title: MVC, HTTP, CQRS
---

MVC (Model-View-Controller) is one of the most well-known and least understood decomposition patterns. 

Initially it was used in "fat" client applications. Model, View, and Controller in such applications were all loaded in memory, and could interact immediately: 

![MVC on fat clients](/images/MVC_fat_client.png)

This is how original (correct) MVC interaction in fat clients works:
* User clicks on button in UI, which triggers Controller action
* Controller action triggers some business logic on model Model, Model changes it's state
* Since View *observes* Model, it's automatically re-rendered
* User sees new UI 

Such simple design had following benefits:
* Presentation Layer (View and Controller) is separate from business logic (Model)
* Model does not know anything about its presentation
* Controller does not know anyting about View, it only interprets user input and passes it to Model.
* CQRS (Command Query Responsibility Segregation) principle is followed: state-modifying infrastructure (Controller) is different from state-receiving infrastructure (View), their complexity can be managed separately.

Later MVC was adopted for web applications. Some of the web-framework implementations were completely wrong: 

![Completely wrong implementation of MVC on server](/images/MVC_Server_HTTP_Completely_Wrong.png)

There are couple problems with such implementeation:
* state modification and state representation both happen in one web request. This is violation of HTTP protocol.
* Controller does all the communication. It knows about both Model and View. It violates CQRS and combines complexity of View and Controller.

By design, HTTP protocol follows CQRS principle: commands (POST, PUT, DELETE) must be separate from queries (GET). So if we'll follow HTTP, we will follow CQRS on communication layer:

![Wrong implementation of MVC for HTTP](/images/MVC_Server_HTTP_Wrong.png)

Here data retrieval request (GET) is separated from data modification (POST), but Controller is still an entry point for both, which is violation of CQRS on application level. Most modern web frameworks are built this way.

To build a proper client-server MVC, one simple step is needed: remove Controller from data retrieval request.

![Correct implementation of MVC for HTTP](/images/MVC_Server_HTTP.png)

You can see that this diagram is almost identical to initial correct fat-client MVC diagram. Such implementation of MVC is correct:

 - Controller only does state modification.
 - View only does state representation.
 - Both respond to request directly.

We can see that both MVC and HTTP follow CQRS principle.

If we apply CQRS further, we will separate our business operations infrastructure from reporting:

![CQRS applied to web application](/images/MVC_Server_HTTP_CQRS.png)

This approach allows to build more scalable applications. One of the possible furhter evolution options is Event Sourcing architecture.
