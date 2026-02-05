- before running and loading configuration, an asp.net app will first determine in which type of environment it is running on
- environment types: Development, Staging, Production
- the app behavior might change based on the runtime environment

# important
- the [[environment variables]] `DOTNET_ENVIRONMENT` determines the runtime environment
- in linux, environment variables are case-sensitive