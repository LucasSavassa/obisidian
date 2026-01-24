# constructors
- user
- authentication
- authorization
- [[identity claim|claims]]
- policy
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

## 7. the user attempts to access another inner area
the access card is prompted and allows calculating if the authenticated user has access to this inner area

## 8. the proxy id is checked against policies
- each inner area may have different access rules (policies)
- a policy is a collection of rules
- the access rules are claim-based
- to determine if an user has access to an inner area, the claims in its identity are verified against the policy rules
![[asp.net.core.identity.security.concepts 2025-12-02 17.15.01.excalidraw]]