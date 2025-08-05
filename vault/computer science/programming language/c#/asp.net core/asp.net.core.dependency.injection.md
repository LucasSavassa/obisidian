- asp.net core implements a built-in DI container
- services have one of the following lifecycles:
	- **transient**: a new one every call
	- **scoped**: a new one per http request
	- **singleton**: one during the entire app lifetime

- to add a service to the DI container:
```
builder.Services.AddScoped<IService, Service>;
```

- to use the registered service in a class:
```
private readonly IService _service;

public Example(IService service)
{
	_service = service;
}
```