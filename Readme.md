# System design Course

# Introduction

This is a fully System design course form FreeCodeCamp that will permit me to go from a simple dev to a simple **App Architecure planner** So the this is mainly and advance skill in 2026 
**Note : From all the analyse  and cherches and did this course is the most relevant course in 2026 For anyone  in 2026 since we  the up coming of AI and new technologies the skill of wrting of code is not more a very valale skills.So i need to build apps base on scalability and furtur updates**
An app with a bad architecture in 2026 mainly a **SAAS(Software as a service)** Is not well designed  will failed and become messy let take the came of app like **ChatGPT** that response to billons of requests everyday do the used of proper and  revolutional architecture made software evoluate today at the great let imagine and app the crash just for a simple request so the main reason of this course this for all ths system designed for applications.

**It is the most revelant Skills in 2026**.I even listen for a friend that companies does not mainly pay 6 figures for developpers that can only code for the need someone can designed and scale their architecture for scarth and so adapt to the market change and time
This is course is been divised into small paths : 

1. The Foundations
2. API Design where API(Application Programming Interfact)
3. Database (Choosing the databse according to the workflow we need to handle)
4. Caching (mainly how to used caching CDN,Load Balancing,redis)
5. Dig-data( I will learn more on it in this course)
6. Production Infra (How to build reproduction ready infractures)

# Single Server Setup

**Now we gonna design a system that has the capacity to handle a single user in practices**
When we talk about a single server setup that means our Webapp,Database,Cache runs on the same server single server.Single server setup are generally used for setting up applications that will not have a great number of users,We know our apps is been divised into **Frontend and a Backend** when the Frontend is the UI of the app and Backend the logic behind the app.So on a single server we have app with Front and Backend that communicate the **Database and the cache via API's that handles the user requests**.When a requests is been made by the user it passes by the address of the server which is been given a **DNS (Domain Name System)** which permits this routing that will redirect the user requests to the app.The request will be send generally as a Http form it call be a **POST,GET,PUT,DELETE,PATCH Request** the user is making to the server and then waiting for it.

**Identifty Traffic** 
If the request is from a web app then the response given mainly comes form the treatement of **HTML,CSS and Javascript**.While for phone request uses API Calls  and response are been send back into json format.
From this module we can cleatly understand that when desiging start small so that the product can be ship easily and fast then scale if needed.

# DataBase Choices

If we face and increase in the number of user into our app that means we need to handle more requests that can slow up our app.So when we facing that we seperate the database from the main app.So we gonna have :

- Application Server (The web and mobile apps)
- The Database Server for handling the app new tough storage 

**Note : This means single app server work great with SQLite as DB**

**Choosing the Right Database** :
We mainly have 2 types of Database that is :

1. Relational Database :
   - SQlite
   - MySQL
   - PortgreSQL
   - MariaDB
2. Non-Relational Database :
   - Mongodb(Mostly Used)
   - Cassadra
   - Redis 

With Relational DB this used structure query languages for Database communication,Connections an building.Data is been store in tables**This is the most stable and most widely used**.
SQL Support Join Operations and permit to create newtables out of relations with others. All this is capable due to the notion of **PRIMARY KEYS AND FOREIEN KEYS**.
SQL DB also come with **ACID principle(Atomicity,Consistency,Isolation,Durablity)**.

**NO-SQL DB**
Let Start with Mongodb which the mostly used non-relational database **MongoDB** stores data as documents do the tables here can be consider as documents and this tables are been return and as json objects.While **Cassadra** stores informations as wide column Other like redis is stores key values and really really fast that is the main reason it is been used for rapide cache storage in our apps.

A DB that i have never used and it seen new to be is **Neo4j** which is been defined as a graphical db which mainly stores informations in a Graph that is **The relations between the differcent tables is been represented as  graphes** Big tech companies like amazon offers usesd this technology.

The Non-relational database offers some advantages like the capacity of storing the tables relations into a single document(json) so intend of having 2 tables we will only have a single json documents that will contain all the informations of the 2 tables.
So good use-case of Relational DB over Non-relational DB : 

- Ecommence Web app
- Management Tracking app
- In fact for app using transactions since we need clean tables that will guide the buyers and the customers

Some advantages and Non-Relational-DB are :

- It low latency so it is vety fast in responding 
- Since data is unstructures is very easy to scale as compare to strict tables

# App Scalaing (Vertical and Horizontal Scaling)

**What is app Scaling** 

App scaling this the process where by we increase the resources that are been used by our apps.This happens where the actual resource benn used by an application becomes insufficient.

We have mainly two types and Scaling that **vertical and horizontal scaling**

**1. Vertical Scaling(Scale up)**
This is the process where by we just allocate more resource to our server that is updating it actual capacity which mainly means incresing it **RAM and Storage Capacity** Let consider our server had a storage of 512GB and 16GB RAM,Vertical scaling will be a update of 512GB for 2TB Storage and also for 16GB to 64GB RAM :

- 512GB  -->  2TB (Storage)
- 16GB   -->  64GB (RAM) 

This method is very classic for app with low traffics and mainly for a single server app is it good but if our app needs for power or requests more power it can turn down our server.

So we still update our server and still faces limitations after sometimes that is where **Horizontal scaling comes in Since our machine will face a limited RAM and Storage Capacity**

**2. Horizontal Scaling**
 With Horizontal Scaling also called **Scale out** we are just adding other server to balance the load traffic of our app and it generally comes after vertical scaling since single server cannot more handle our app we use multiple ups which can be scale up later is just pure magic That is :

- Intend of using 1 server for our app we can balance it traffic on 2 or 3 server so that if server 1 fall the app service state up.

**Note : Horizontal scaling comes with a better scalabilty but is mainly more sweetable for large scale app since we only need to add more servers to our app**

# Load Balancing

We said ealier that we gonna Used Horizontal scaling in situation of high traffic but for this type of scaling we mainly need to distrubute the charges within the servers for that we need  to insert a **Load Balancer** between the server and the App requests.
**What is the role of the Load Balancer ??**
The load balancer has the main function to distribute the charges within the accoring to the traffic demand that is when i have an application the traffic that comes from the mobile device is always higher so i will takes higher resourcesthat is more **RAM and More storage for the app to be responsive and fast**.So the load balancer will be responsible of this process of traffic distribution.

To Understand Load-Balancibng we need to look at 7 Algorithm that are commonly used in Load Balancing.

1. **Round Robin:** Here the Load Balancer distribute the request according to sending order that is if the **n-requests** are been send to the load balancer then request n1 is been send to server one,request n2 to redirect to server2,and request n3 to server 3 and that is how to goes on.**This is the principle of Round Robin**

2. **Least Connections:**  Here traffic is been redirected to the server with the least active connection or the least traffic on it.That is if :
   
   - Server1 has 20 active connections
   - Server2 has 9 active connections
   - Server3 has 50 active connections
     Them for the principle of **Least Connections** the request will be automatically redirect to Server2 since it only has 9 active users this is a more stable algorithm for load balancing.This is very useful for applications where users hassessions to do.

3. **Least Responsive Time:**  This algorithm is base on the response time of the servers we made have server with **high,mid and low responsive time**
   So here the load Balancer will send request to the high resonsive server first then control the number of connections on it.If full then the server will route the requests to the mid resonsive then if full connections then the low responsive server.But Note that a High response server can handle maybe 100 requests in 1ms while the mid do that in 5ms and the low in 15ms so always takes that in consideration.

4. **IP HASH:** 
   This algorithm is base on the ip hash of the users to the server so server are pre-configurated to receive a  particular **IP-HASH** So here the load redirect traffic according to setup configs for this balancing accoring to the **user ip hash** That means the load balancer uses more login.This is very useful in the way in the case where by a user will that has been connected to a particular server will be redirected to that server for his next session directly.

5. **Weigthed Algorithm**
   This algorithm is base on the resources of each servers like if server1 has 16GB RAM,server2 32GB RAM and Server3 64GB then the Load Balancer will have the role to weight and asigned the request to the server according to the capacity each server can handle.That is from the 64GB server to the 16GB server.

6. **Geographical Algorithms**
   This algorithm is really simple here requests are been handles within Geographical Locations that is : 
   If a request comes from a user in Europe he will redirect to the server that handles it zone,While user that comes from the USA will be redirected to the USA server.

7. **Consistent Hashing** 
   This is the most popular hashing algorithm and mainly uses the hashing functions which hashes the user request and redirect to the nearest server to which te user has connected so this algorithm uses **A Hashing Cycle**

# Health Checks

Since we have many Server we need to monitor them and the lourd balancer mainly have this capacity of **health check Intergrated to it** so the load balancer which is been connected to servers can monitor and check the status of our various servers.So if a server falls in our architecture we will know about it.So we can easily do backup operations if we know that our server can fall and by checking it activity and health so we can insert so backup server so that if the principal fails the backup server will takes the lead of the operations.With this process and using Algorithm we call up with higher server routing logic.

For this processing of Load Balancing we mainly have mainy methods like **Software Load Balancing**  with the used of a Software like **Nginx** For more informations we can find that on the Nginx web site.Nginx can used directy on our workflows architecture using a docker images for our simple app deployment. 
Another example of a Load Balancer is **HA proxy** and also the **AWS Elastic Load Balancing,Azure Load Balancer and Google Cloud Load Balancer**

# Single point of Failure

Let us return to our system course design and go back to the concept of **SPOF** which means Single point of Failure which is been defined as any component which will cause the whole system to fails if it falls.So it is a critical issue in System designed.
If we consider an architecture where our users pass by the load balancer before reaching the servers if the load balancer fails the whole systel is down but the load balancer generally have a monitoring system but **if the servers of the system is been linked to be single Database if that DB fails the whole system will fails** Which means here our DB is a our single point of Failure.
Systems with single points of failure also facing problem with scalability and security issues like an attacker can send alot of traffic to the load balancer to saturate the system and brings it down.

To avoid SPOF on load balancer we can used the following options : 
1. Redundancy : 
That is adding more load balancer  in other architecture so that if one balancer fails users will be redirected to another one until the connection is back 
2. Health Check & Monitoring :
This is the most common and simple wait to prevent our system to fails 
3. Self-Healing System : 
This is when a Load balancer falls and redirects the traffic to an instance of another load balancer which is mainly a copy that contains all the informations of that load balancer.


# API Design 
 This is a very important session in system design and the type of API used in a sytem depends mainly on what we have to build.

**What is an API**
API(Application Programming Interface) Simply defines how software components should interacts.
API stands between the clients and the servers and it define what type of requests is  been made by the client to the server,how to make that requests and also what type of response should we except.
Thats is mainly the role of an API in an our APP.Example 
**Use user making a GET request except to get back data in return**.API also set up the services boundaries since it defines clear interfaces between system components.

**Types of API**
We mainly have 3 main types of API :
**1. RESTAPI**
**2. GRAGHQL**
**3. gRPC** 

They most commonly used API here  is the RESTAPI which uses resource base organise around resource using HTTP methods.
The main advantage of RestAPI is that the are stateless that means each request contains all of the informations needed.
RESTAPI also have Standardize methods that is we already know what method we gonna used of working with RESTAPI that is **GET,POST,PUT,DELETE,PATCH e.t.c** .RestAPI are mostly used in Web and Mobile Apps.


**GRAPHQL**
This is mainly a **Query language** which is has the main purpose of allowing the client to get the exact piece of information he/she want to get with precitions.
There have single end-points that is one **End-point for an Operation**.Also the operation here can called **Query(reading data),mutations(wrting data),subcriptions** which are the equivalent of PUT,PATCH in RESTAPI.
GRAPHQL is been used in **Complex UIs**


**gRPC**
This is the least commann type of API.It is a Protocol Buffers which means it can used **Binary serailization with schemas defintions**
Here methods are been defined in a file called the **.proto files**.For the communications types we mainly uses **Client Streaming,Bidirectional Streaming etc** 
It is a high performance API used in **Microservices**


**REST vs GRAPHQL**
RestApi always comes with resource base endpoints which can user  or an item.Need multiple request to get the related data.With HTTP methods the definitions for the oprations is quite simple.The response structure are fix,provide expicit versionning while GRAPHQL comes with a single endpoint for all it operations and also uses Query languages for operations,has a schemas evolution with versionning,Single request are done for preside data.


**4 Key Design Principles**
There 4 Principle of a Good API is that it should be : 
**1. Consistency**
  - Consistent naming 
  - Consistent pattern
**2. Simplicity**
  - Focus on Core users
  - Intitutive design
**3. Secutity**
  - Authentification
  - Authorization
  - Input Validation
  - Rate liming
**4. Performance**
  - Caching Stability
  - Pagination
  - Reduce round tips 

**Note : A Good API is an API That developpers can used without reading it documenation**

Each of this API uses **API protocols** So the API protocols used mainly infleunce the architecture we will build for our apps.
After all this we gonna move to the API design process and then move to Design Approches like **Top-down(From high standards to lower ones) method or Bottom-up(From Low standards to high ones) method**
We will also see the Life_cycle of APIs.The big of a API dev is not coding but designing it.




# API PROTOCOLS



