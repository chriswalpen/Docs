# InjectionMap
------------------------------
InjectionMap is a very small and extremely lightweight IoC/DI container for .NET. 
InjectionMap allows loose coupling betweeen a client's dependencies and its own behaviour. InjectionMap promotes reusability, testability and maintainability of any part of an application.

- InjectionMap is a very lightweith IoC Framework that leaves no traces in the client code
- InjectionMap uses type mapping to reference the contract and the implementation. 
- Instances are resolved using reflection or can be provided through a callback whitch allows the creation of instances in your own code.
- It suports a fluent syntax to help keep the code simple, small and clean.
- Parameters for constructors can be injected or passed at the time of mapping as objects or as delegate expressions.
- InjectionMap is very simple and straightforward.
- Allows mapping to a custom MappinContainer. This can help to prevent the ServiceLocator anti-pattern

InjectionMap supports .Net 4.5, Silverlight 5, Windows Phone 8 or higher and Windows Store apps for Windows 8 or higher.

## Installation
------------------------------
InjectionMap can be installed from [NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) through the package manager console:  

    PM > Install-Package InjectionMap
