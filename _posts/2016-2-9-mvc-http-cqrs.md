---
layout: post
title: MVC, HTTP, CQRS
---

MVC (Model-View-Controller) is one of the most well-known and least understood decomposition patterns. 

Initially it was used in "fat" client applications. Model, View, and Controller in such applications were all loaded in memory, and could interact immediately. Important thing about MVC was that all three components were completely decoupled and every component knows about only one other component: Controller knows about Model, Model knows about View, View declares user actions that trigger Controller Actions. 

![MVC on fat clients](/images/MVC_fat_client.png)

This is how original (correct) MVC interaction in fat clients works:
* User clicks on button in UI, which triggers Controller action
* Controller action triggers some business logic on model Model, Model changes it's state
* Since View *observes* Model, it's automatically rerendered
* User sees new UI

Later MVC was adopted for web applications. Some of the HTTP implementations were completely wrong: 

![Completely wrong implementation of MVC on server](/images/MVC_Server_HTTP_Completely_Wrong.png)

Notice that state modification and state representation both happen in one request. This is violation of HTTP protocol. Also Controller does all the communication. View does not observe Model. 

Many of those, who followed HTTP rules, came up with following communication:

![Wrong implementation of MVC for HTTP](/images/MVC_Server_HTTP_Wrong.png)

Here data retrieval request is separated from data modification, but Controller is still an entry point for both. This is how most modern web frameworks are built.

If we remove Controller from data retrieval request, we will come up with diagram almost identical to original "fat" client diagram above:

![Correct implementation of MVC for HTTP](/images/MVC_Server_HTTP.png)

Such implementation of MVC is correct:

 - Controller only does state modification
 - View only does state representation
 - Both respond to request directly.

Last diagram demonstrates that for both MVC and HTTP data modification and data representation are separated. They are both following CQRS (Command Query Responsibility Segregation).

If we apply CQRS further, we will separate our business operations infrastructure from reporting:

![CQRS applied to web application](/images/MVC_Server_HTTP_CQRS.png)

This approach allows to build more scalable applications. One of the possible furhter evolution options is Event Sourcing architecture.
