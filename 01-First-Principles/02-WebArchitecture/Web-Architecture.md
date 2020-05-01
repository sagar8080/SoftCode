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
### Single Page Applications
* Instead of loading completely new pages from the server each time for a user action, single page web applications allows for a dynamic interaction by means of providing updated content to the current page.

* Makes use of AJAX and Jquery a lot, a concise form of Asynchronous JavaScript and XML, is the foundation for enabling page communications and hence, making SPAs a reality.

* Because single-page applications prevent interruptions in user experience, they, in a way, resemble traditional desktop applications.

* SPAs are designed in a way so that they request for most necessary content and information elements. This leads to the procurement of an intuitive as well as interactive user experience.

### Microservices
* These are small and lightweight services that execute a single functionality.
* The Microservices Architecture framework has a number of advantages that allows developers to not only enhance productivity but also speed up the entire deployment process.
* The components making up an application build using the Microservices Architecture aren’t directly dependent on each other. As such, they don’t necessitate to be built using the same programming language.
* If you are working with the Microservices Architecture, you are free to pick up a technology stack of choice. It makes developing the application simpler and quicker.

### Serverless Architectures
* In this type of web application architecture, an application developer consults a third-party cloud infrastructure services provider for outsourcing server as well as infrastructure management.
* The benefit of this approach is that it allows applications to execute the code logic without bothering with the infrastructure-related tasks.
* The Serverless Architecture is best when the development company doesn’t want to manage or support the servers as well as the hardware they have developed the web application for.

## How the request response cycle works
Lets say you wish to visit a site called XYZ.com

1. First, you visit XYZ.com.
    * You type in the URL and as you hit Enter, your browser prepares to recognize this URL, because it needs to know the address of the server where the page is located.
    * So it sends your request to the Domain Name Center (DNS), a repository of domain names and their IP addresses.
    * If you’ve already visited XYZ from the same browser, it will pull the address from the cache.
    * Then, a browser sends the request to the found IP address using the HTTPS protocol.

2. Second, the web server processes the request.
    * The web server where XYZ.com is located catches the request and sends it to the storage area to locate the page and all data that follows with it.
    * But its route is held via Business Logic (also called Domain Logic and Application Logic).
    * Business Logic manages how each piece of data is accessed and determines this workflow specifically for each application.
    * As Business Logic processes the request, it sends it to storage to locate the looked-for data.

3. Third, you receive your data.
    * Your response travels back to you and you see the content of the web page on your display.
    * The graphical interface you see when scrolling XYZ’s or any other website is called the front end of an application – it depicts all UX and UI components so that a user can access the information they came looking for.
