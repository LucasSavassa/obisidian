![[asp.net.core.authentication 2025-07-09 18.59.10.excalidraw]]
- the authentication middleware runs the registered authentication service
- the authentication service runs the registered authentication schemes (*handlers*)
- schemes can be registered in `program.cs`
![[asp.net.core.authentication 2025-07-09 19.13.20.excalidraw]]
- an scheme builds an authenticated user from claims, http request, context ...
- authorization uses the authenticated user `ClaimsPrincipal` to authorize actions
- authorization can reference which authentication scheme to use by scheme name

```csharp
builder.Services.AddAuthentication();

var app = builder.Build();

app.UseAuthentication();
...
app.UseMiddlewareDependentOnAuthentication1();
app.UseMiddlewareDependentOnAuthentication2();
```

## authentication scheme
- authentication scheme determines user
- authentication handles user to authorization
- authorization determines if user is authorized
- if authorized, page is delivered to browser
- if authenticated but not authorized, authorization invokes authentication's prohibits handler
- if not authenticated and needs authorization, authorization invokes authentication's challenge handler
![[asp.net.core.authentication 2025-07-09 19.39.05.excalidraw]]
