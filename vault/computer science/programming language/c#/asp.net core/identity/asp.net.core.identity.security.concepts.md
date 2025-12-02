# constructors
- user
- authentication
- authorization
- [[asp.net.core.identity.claim|claims]]
- access
- roles
 
# flow
![[asp.net.core.identity.security.concepts 2025-11-25 13.24.37.excalidraw]]
## 1. attempt enter
an anonymous and disguised user attempts to access a secured area

> [!info] in this case
> a web site

## 2. prompt identity
the anonymous user (unauthenticated) is prompted for identity hints (claims)

> [!info] in this case
> - user name
> - user email
> - user password

## 3. provide identity

## 4. validate identity
the security validates if claims are legitimate and if they identify a known, registered individual

## 5. allow enter

## 6. provide proxy id
the security generates a unique access card with information about the individual. the access card exempts initiating another authentication process inside the secured area

> [!info] in this case
> - cookie
> - json web token

## ?. the user attempts to access another inner area
the access card is prompted and  allows calculating if the authenticated user has access to this inner area