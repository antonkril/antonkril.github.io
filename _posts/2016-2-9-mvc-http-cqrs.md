---
layout: post
title: MVC, HTTP, CQRS
---

MVC (Model-View-Controller) is one of the most well-known and least understood decomposition patterns. 

Initially it was used in "fat" client applications. Model, View, and Controller in such applications were all loaded in memory, and could interact immediately:

![MVC on fat clients](/images/MVC_fat_client.png)

Here Action updates Model, and View is re-rendered immediately because it observes the state of the Model.

Later MVC was adopted for web applications. Some of the HTTP implementations were completely wrong: 

![Completely wrong implementation of MVC on server](/images/MVC_Server_HTTP_Completely_Wrong.png)

Notice that state modification and state representation both happen in one request. Also Controller does all the communication. View does not observe Model. This is violation of HTTP protocol.

Many of those, who followed HTTP rules, came up with following communication:

![Wrong implementation of MVC for HTTP](/images/MVC_Server_HTTP_Wrong.png)

Here data retrieval request is separated from data modification, but Controller is still an entry point for both. This is how most modern web frameworks are built.

If we remove Controller from data retrieval request, we will come up with diagram almost identical to original "fat" client diagram above:

![Correct implementation of MVC for HTTP](/images/MVC_Server_HTTP.png)

This implementation of MVC is correct:

 - Controller only does state modification
 - View only does state representation
 - Both respond to request directly.

Last diagram demonstrates that for both MVC and HTTP data modification and data representation are separated. They are both following CQRS (Command Query Responsibility Segregation).

If we apply CQRS further, we will separate our business operations infrastructure from reporting:

![CQRS applied to web application](/images/MVC_Server_HTTP_CQRS.png)

This approach allows to build more scalable applications. One of the possible furhter evolution options is Event Sourcing architecture.
