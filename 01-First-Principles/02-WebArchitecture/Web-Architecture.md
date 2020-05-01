# Web Application Architecture

It is of utmost importance to be aware of how any web application works, it will aid a lot more to your design concepts.
As a developer you have to take into account anything and everything that simplifies and boosts the user experience.
I'll cover the design aspects in the System design concepts.
The core of a Web application is its server-side logic.
The Web application layer itself can be comprised of many distinct layers.
The typical example is a three-layered architecture comprised of presentation, business, and data layers.
![web architecture](SoftCode/01-First-Principles/02-WebArchitecture/pictures/Webarchitecture-01.png?raw=true)

## User - Developer conondrum

User’s requirements generally concentrated on usability.
It includes time used for updating information on pages, ability to switch between pages or save links and bookmarks and options for offline work.

Developer’s requirements are mainly concentrated on performance, scalability and development speed.
Introduce new features, restructure the code and parallelize the software development process, minimize the server’s response time, increase computation power, provide consistent and available data.

## Reason of having an web-app architecture

* The basics of any web architecture is the segregation of application components into `user-interface` and `structure`
* The components of the structure link the internet browser or client, the application server, and the database server.
* The user or the internet browser deals with the app performance of interaction with the client.
* It functions by applying JavaScript, HTML or CSS.
* An important thing to notice here is that it doesn’t require any adaptations for the operating system.
* The browser is like the interaction channel for the clients.
* The server is the control center to manage layered applications and you can use a variety of languages: Ruby,    Node.js, Python, .Net, PHP They will help to manage data persistence and business logic.

## Web Application Components
When we say web application components, we can mean any of the following two:

* `UI/UX Web Application Components` – This includes activity logs, dashboards, notifications, settings, statistics, etc. These components have nothing to do with the operation of a web application architecture. Instead, they are part of the interface layout plan of a web app.

* `Structural Components` – The two major structural components of a web app are client and server sides.

  * `Client Component` - The client component is developed in CSS, HTML, and JS. As it exists within the user’s web browser, there is no need for operating system or device-related adjustments. The client component is a representation of a web application’s functionality that the end-user interacts with.

  * `Server Component` - The server component can be build using one or a combination of several programming languages and frameworks, including Java, .Net, NodeJS, PHP, Python, and Ruby on Rails. The server component has at least two parts; app logic and database. The former is the main control center of the web application while the latter is where all the persistent data is stored.

### Models of Web Application Components
Depending on the total number of servers and databases used for a web application, the model of a web app is decided. It can be any of the following three:

#### One Web Server, One Database
* It is the most simple as well as the least reliable web app component model.
* Such a model uses a single server as well as a single database.
* A web app builds on such a model will go down as soon as the server goes down and isn’t much reliable.
* One web server, one database web application component model is not typically used for real web applications.
* It is mostly used for running test projects as well as with the intent of learning and understanding the fundamentals of the web application.

#### Multiple Web Servers, One Database (At a Machine Rather than the Web server)
* The idea with this type of web application component model is that the webserver doesn’t store any data.
* When the webserver gets information from a client, it processes the same and then writes it to the database, which is managed outside of the server.
* This is sometimes also referred to as a stateless architecture.
* At least 2 web servers are required for this web application component model.
* This is all for avoiding failure. Even when one of the web servers goes down, the other one will take charge.
* All requests made will be redirected automatically to the new server and the web app will continue execution.
* Hence, reliability is better as compared to the single server with inherent database model.
* However, if the database crashes the web app will follow to do the same.

#### Multiple Web Server, Multiple Databases
* It is the most efficient web application component model because neither the webservers nor the databases have a single point of failure.
* There are two options for this type of model:
  * Either to store identical data in all the employed databases or
  * distribute it evenly among them.
* Not more than 2 databases are required typically for the former case, while for the latter case some data might become unavailable in the scenario of a database crash. DBMS normalization is used, however, in both scenarios.
* When the scale is large i.e. more than 5 web servers or databases or both, it is advised to install load balancers.

## Models
### Client - server Models
Initially the web consisted of this two tiered architecture
