# .NET


## .NET Conventions
##### [NET-CONV] [A]
- [Codaxy C# Coding Conventions](conventions.md)

## C# 

##### [NET-CS] [A]
- [Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)) and [access modifiers](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)
- [Properties, getters, setters](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties), 

##### [NET-CS-02] [C]
- [Read-only auto-properties](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-6#read-only-auto-properties)
- Value types, reference types
- Static fields, static classes
- Extension methods
- Collections and other useful data types
- Linq

##### [NET-CS-03] [D]
- Generics
- Async / await
- Serialization, JSON.NET
- Named tuples, deconstruction
- Covariance, contravariance

#### Useful resources
- [C# 7.0 in a Nutshell](https://www.amazon.com/C-7-0-Nutshell-Definitive-Reference/dp/1491987650)
- https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-8


## Best practices
##### [NET-BEST] [D]
- SOLID
- [Concise code (Skeet C#)](https://freecontent.manning.com/c-in-depth-4th-edition-concise-code-with-local-methods/)
- DateTime / DateTimeOffset pitfalls

## ASP.NET Core
##### [NET-ASP] [DE]
- Core concepts
- Application lifecycle, pipeline/middleware concept, Startup.cs
- Cookies: basics, authorization, localization
- Configuring DI beyond default, Autofac
- Environment-specific configurations--best practices

## ASP.NET Core Web API
##### [NET-API] [C]
- Models, controllers
- [HTTP verb mapping](https://restfulapi.net/http-methods/)

##### [NET-API-02] [D]
- Proper routing conventions
- AutoMapper

## ASP.NET Core MVC
##### [NET-MVC] [C]
- Models, controllers, views
- Razor

##### [NET-MVC-02] [D]
- Layouts
- Razor pages, ViewModels, DI into pages

## Dependency injection
##### [NET-DI] [DE]
- IoC / DI
- Scope lifetime, `LifetimeScope`
- `Autofac`
- On-demand instantiation, (`scope.Resolve`)
- Bulk registration (`RegisterAssemblyTypes`), named registration, typed registration
- Resolving contructor parameters, autofactories

## Design patterns
##### [NET-PAT] [DE]
- Factory, DI, Repository, Singleton, Command, Behavior, Mediator, Observer

## Error handling
##### [NET-ERR] [DE]
- Exceptions, log and rethrow
- Error handling filters (KnownExceptionHandlingFilter)
- Best practices: typed Exceptions (UserFriendlyException, ItemNotFoundException)

## Logging
##### [NET-LOG] [DE]
- DI approach
- Configurable loggers (appsettings)
- Structured logging
- External targets (e.g. Seq)

## Entity Framework
##### [NET-EF] [DE]
- Code First, migrations
- Scaffolding from existing databases

## Security
##### [NET-SEC] [DE]
- Authentication and authorization
- OAuth 2
- Cookies
- Tokens
- Refresh token pattern and antipattern
- Secured controller actions

## Testing
##### [NET-TEST] [E]
- xUnit, Facts and Theories
- Unit tests
- Integration tests
- DI and mocking
- e2e tests

## Application architecture
##### [NET-ARCH] [E]
- Services, separation of concerns
- Stateless applications
- Object lifetime
- Caching (Redis, memcached)

#### Useful resources
- [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)--many useful concepts illustrated in this reference implementation
- [NorthwindTraders](https://github.com/JasonGT/NorthwindTraders)--slightly less overwhelming, yet very good reference implementation of a relatively complex architecture

## Localization
##### [NET-LOC] [DE]
- Resource localization (`.resx`)
- Culture cookies, request params, HTTP headers
- Culture-dependent formatting (UICulture)
- ASP.NET Core MVC

## Concurrency
##### [NET-CONC] [E]
- Multithreading
- Synchronization mechanisms (lock, monitor)
- Background tasks

## IIS
##### [NET-IIS] [E]
- Hosting ASP.NET Core apps

## Microservice architecture
##### [NET-DDD] [EF]
- Loose coupling
- Domain objects, business logic
- Containerization, Docker
- Resilient application, partial failure handling, exponential backoff
