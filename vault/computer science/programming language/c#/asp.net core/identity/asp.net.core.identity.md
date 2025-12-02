[[asp.net.core.identity.security.concepts|security concepts]]
[[asp.net.core.authentication|authentication]]
# references
[docs](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/identity?view=aspnetcore-9.0&tabs=visual-studio)
[code](https://github.com/dotnet/AspNetCore/tree/main/src/Identity)
# plan to understand this shit
- [ ] understand identity architecture
	- [x] list goals
	- [ ] how goals breakdown into actions
	- [ ] derive objects
	- [ ] connect objects and actions
- [ ] understand identity ui
# goals
- use http request + context to determine user identity (authentication)
- create and manage session
- use user identity to authorize or block content to user (authorization)
- a framework that provides code to securely authenticate and authorize users
- implements best practices
- provides boilerplate user interface
# asp.net core identity vs oidc
## asp.net core identity
asp.net core identity uses databases
asp.net core identity serves only the asp.net core app that declared it
## oidc
[oidc](https://www.microsoft.com/en-us/security/business/security-101/what-is-openid-connect-oidc) provides **single sign-on**
![[Pasted image 20250919091501.png]]
oidc is a protocol that extends oauth2
oidc can provide authentication services to multiple apps (multi-tenant)
oidc authenticates the user, then builds a claim, then turn it into a token
## how to choose
check [this article](https://learn.microsoft.com/en-us/aspnet/core/security/how-to-choose-identity-solution)

# migrations
to use the identity api, asp.net core apps must define a connection with a database that implements the identity schema. if the dabase doesn't contain the schema yet, then [[asp.net.core.entityframework#migration|entity framework migrations]] can be used to apply it.