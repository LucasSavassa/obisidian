[source](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/?view=aspnetcore-9.0&tabs=windows)
# program.cs
- asp.net core apps contain a **program.cs** files
- this file is the starting point for execution
- this file contains code to execute these tasks:
![[asp net program.cs file]] 
**services** are declared in the pre configure phase
**middleware** is declared in the pos configure phase
# dependency injection (DI)
when a service is added to the app
```csharp
builder.Services.AddService();
```
it becomes available in a global scope
in other words, it can be accessed (*resolved*) everywhere
**razor**
```razor
@inject IService service
```
**class**
```csharp
class Parser
{
	private readonly IService _service;
	
	Parser(IService service)
	{
		_service = service;
	}
}
```
# middleware
middleware is added using `app.Use{middleware}` pattern
![[asp.net middleware pipeline.png]]
every app executes a middleware pipeline
the middleware pipeline is composed of many middleware services stacked
when a request is received by web server, it passes to the top middleware service
the top middleware service has a chance to act
then the request is handed to the next middleware service
after all middleware had a chance to act, the response is created and passed back to the last middleware in the stack
then each middleware has a chance to process the response
then handles the response to the previous middleware
the endpoint is always the last item in the middleware pipeline
# host
the variable `app` represents a **host**

a host is an object the encapsulates the app's resources:
- dependency injection
- logging
- configuration
- `IHostedService` implementations

![[asp net core host]]
when the host starts, it also starts its services
when the host stops, it gracefully stops other services
when the host is built, asp net core do many things under the hood, [see](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/generic-host?view=aspnetcore-9.0#default-builder-settings)
a web host do some additional things, **like setting [Kestrel](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel?view=aspnetcore-9.0) as the web server**
# server
