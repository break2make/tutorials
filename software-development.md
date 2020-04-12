# Software Development

In application development, it is very common to use framework/libraries/service which provide reusable functionalities that encapsulate lower-level functionalities by providing an higher abstraction to the inner complexities of certain features.

Typically framework/libraries/services stay static within the development of an application, at least besides occasional upgrades, application code utilises the functionality provided by the modules to create a specific behaviour for the logical interaction between users and a domain of data in a generally tighter-defined environment.

So, while the application code is constantly changing as the application evolves and develops, framework, services and libraries provides fundamental building blocks behind the structure of the product.

## Library VS Service

**Library**

- shared code (or object) that you compile (or link) into your application. 
- white box from outside the application (other app knows the code behind)
- no contract (just docu)
- API with code (java, php, javascript, C#, etc)

**Service**
- a shared capability that you access from your application
- is a running system that provies functionality to other sstems
- black box from outside the application (other app doesnt know the code behind)
- contractbased (WSDL, WADL, etc)
- API with application protokol, dataformat (JMS, HTTP, XML, JSON, etc)

The agility, reuse, and transparency benefits of a service are just too hard to ignore. However, there are specific cases where creating libraries could be more appropriate:
- When you’re building an application that will be deployed to a device with inconsistent network access (making remote service consumption unreliable)
- When you’re building an application that will be hardened with wrapper technology for security reasons (and network access to remote services is seen as an unacceptable compromise)

For a detailed comparion between library and services, check this [link][lib-service].

## Library & Frameworks: its a matter of control

As explined by Daniele Margutti in his [post][lib-framewrok-iquii]:

The key difference between a library and a framework can be summarised in a word: IoC — Inversion Of Control.
- When you use a feature from a library you are in control.
- With a framework the control is inverted; the framework use you: it’s just like The Hollywood Principle: “Don’t call Us, We’ll call You”.

Software framework can be defined as an architecture which facilitates implementation of software in a well organised manner.

In fact a *framework defines a skeleton where the application defines its own features to fill out the skeleton.*

> **Frameworks thus emphasise design reuse over code reuse.**

## API

An API acts as an interface between two different applications so that they can communicate with each other. An API is a method by which the third-party vendors can write programs that interface easily with other programs.

An API exactly defines the methods for one software program to interact with the other. When this action involves sending data over a network, Web services come into the picture. An API generally involves calling functions from within a software program.

> **There are many situatons, where API does not involve any implementation, it is simple a specification how to use a functionality of a library.**


[lib-framewrok-iquii]: https://medium.com/iquii/applications-vs-frameworks-vs-libraries-c1f1a6122711

[lib-service]: https://blogs.gartner.com/eric-knipp/2013/03/20/libraries-vs-services/

## Important Resources
- [Libraries vs. Services][lib-service]
- [Applications vs Frameworks vs Libraries][lib-framewrok-iquii]
- [Framework vs Library vs Platform vs API vs SDK vs Toolkits vs IDE](https://medium.com/@programmerasi/difference-between-api-and-web-service-73c873573c9d)
- [Web Service vs. Shared Library
](https://stackoverflow.com/questions/1312825/web-service-vs-shared-library)
- [APIs versus services – is there a difference?](https://developer.ibm.com/technologies/api/articles/api-vs-services-whats-the-difference/)
- [Difference Between API and Web Service](https://medium.com/@programmerasi/difference-between-api-and-web-service-73c873573c9d)