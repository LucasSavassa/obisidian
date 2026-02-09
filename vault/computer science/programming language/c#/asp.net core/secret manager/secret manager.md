[reference](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-10.0&tabs=windows)

- project scoped
- saves to text files
- not cryptographed

# init
navigate to project directory (where .csproj is)
```
dotnet user-secrets init
```

# set a secret
navigate to project directory (where .csproj is)
```
dotnet user-secrets set "{ key }" "{ value }"
dotnet user-secrets set "{ group }:{ key }" "{ value }"
```

from anywhere
```
dotnet user-secrets set "{ key }" "{ value }" --project "{ path }"
dotnet user-secrets set "{ group }:{ key }" "{ value }" --project "{ path }"
```

# list
```
dotnet user-secrets list
```

# remove
specific
```
dotnet user-secrets remove "{ key }"
```

all
```
dotnet user-secrets clear
```