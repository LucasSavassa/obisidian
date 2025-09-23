# context
or dbcontext represents a unit of work (business transaction)
in web apps, 1 http request = 1 dbcontext instance (scoped lifetime)
## configuration
```csharp
var connectionString =
    builder.Configuration.GetConnectionString("DefaultConnection");

builder.Services.AddDbContext<ApplicationDbContext>
(
	options => options.UseSqlServer(connectionString)
);
```
builder.Services.AddDbContext ties model to database
![[asp.net.core.entityframework 2025-09-23 17.59.32.excalidraw]]
# migration
[getting started](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#getting-started)
migration keeps a database in sync with model defined in code
![[asp.net.core.identity 2025-09-22 09.05.36.excalidraw]]

entity framework keeps track of model changes
it compares current model to last snapshot
when changes exists, it can produce a .migration
.migration can be shared
![[asp.net.core.identity 2025-09-23 17.04.08.excalidraw]]