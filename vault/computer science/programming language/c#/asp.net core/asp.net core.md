[source](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/?view=aspnetcore-9.0&tabs=windows)
# program.cs
- asp.net core apps contain a **program.cs** files
- this file is the starting point for execution
- this file contains code to execute these tasks:
![[asp net program.cs file]] 
**services** are declared in the pre configure phase
**middleware** is declared in the pos configure phase
# dependency injection (DI)
asp net provides a dependency injection framework
when a service is added to the app
```csharp
builder.Services.AddService();
```
it becomes available in a global scope
in other words, it can be accessed (***resolved***) everywhere
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
the examples above demonstrate how to **resolve** a service
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
- dependency injection framework
- logging
- configuration framework
- `IHostedService` implementations
- environment framework

![[asp net core host]]
when the host starts, it also starts its services
when the host stops, it gracefully stops other services
when the host is built, asp net core do many things under the hood, [see](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/generic-host?view=aspnetcore-9.0#default-builder-settings)
a web host do some additional things, **like setting [Kestrel](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel?view=aspnetcore-9.0) as the web server**
# server
asp.net core provide three http servers to choose:
- [Kestrel](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel?view=aspnetcore-9.0) *default*
- [IIS](https://learn.microsoft.com/en-us/iis/)
- [HTTP.sys](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/httpsys?view=aspnetcore-9.0)
# configuration
built-in configuration providers:
- .json files *default*
- .xml files
- environment variables *default*
- command-line arguments *default*
- support to custom configuration providers

> environment variables **override** appsettings.json

## secrets
- in **dev** use [secret manager](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-9.0#secret-manager)
- in **prod** use [azure key vault](https://learn.microsoft.com/en-us/aspnet/core/security/key-vault-configuration?view=aspnetcore-9.0)

# environment framework
environment type is defined by environment variable `ASPNETCORE_ENVIRONMENT`
## 1. set environment variable
```powershell
$env:SECRET = "palmeiras nao tem mundial"
```
## 2. access environment variable
``` csharp
var builder = WebApplication.CreateBuilder(args);

string? secret = Environment.GetEnvironmentVariable("SECRET")
```

> asp.net core reads that variable at startup and exposes it

``` csharp
app.Environment.IsDevelopment()
```
# logging
asp.net core imports .net logging framework

and application typically:
1. choose loggers 
2. log data

when the app calls `Log('message')`, all loggers will log

## -1. configure logger
each environment has its own configuration
see [configure logging](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-9.0#configure-logging)
## 0. clear loggers
```csharp
var builder = WebApplication.CreateBuilder(args);
builder.Logging.ClearProviders();
```
## 1. declare loggers
```csharp
var builder = WebApplication.CreateBuilder(args);
builder.Logging.AddConsole();
builder.Logging.AddAzureLogger();
builder.Logging.AddCustomLogger();
```
## 2. resolve logger
```csharp
public class MyClass : PageModel
{
	private readonly ILogger _logger;
	
	public AboutModel(ILogger<AboutModel> logger)
	{
		_logger = logger;
	}
```
## 3. log
```csharp
_logger.LogInformation("information");
_logger.LogWarning("warning");
_logger.LogError("error");
```
