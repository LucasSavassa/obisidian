# reference
![](https://www.youtube.com/watch?v=t18YB3xDfXI&t=60s)
# summary
open id connect (oidc) extends oauth2 to provide authentication services

# fundamental problem
## premises
you have a broker account
you have a financial mentor
## problem
you want your mentor to have access to view your financial data,
but you don't want to give him your password.
how do you do that?

![[oauth 2026-02-10 20.51.09.excalidraw]]
# oauth2 terminology

| concept              | definition                                           |
| -------------------- | ---------------------------------------------------- |
| resource owner       | the user, who wants to share permissions with an app |
| user agent           | e.g. mobile phone, computer                          |
| client               | financial mentor, the app who needs permission       |
| resource server      | broker app, who hosts the data                       |
| authorization server | third party, usually the resource server itself      |
| redirect uri         | where the client lands once given permission         |
| response type        | type of data that the client expects                 |
| scope                | granular permissions (e.g. read data, edit data)     |
| consent              | an formal authorization request prompted to the user |
| client id            | identifies the client with the auth server           |
| client secret        | password that only client and auth server knows      |
| auth code            | a short-lived token that represents the consent      |
| access token         | a token that represents valid access                 |
| id token             | a token that contains user identity data             |
| front channel        | query string                                         |
| back channel         | https post request                                   |
# concepts
- oauth flow
- access token
- id token
- client types
## access token
- issued by oauth
- a token that represents valid access
## id token
- issued by open id connect
- a token that contains user identity data
## client types
- when registering an app in an auth server, you must choose a client type: confidential or public
- the auth will determine how to handle the auth flow. it may issue refresh tokens instead of access tokens in more risky scenarios, or skip the consent in less risky ones
- a confidential client can store a password safely (e.g. web apps, using environment variables)
- a public client can't (e.g. single page apps, mobile apps)

# diagrams
## authorization code flow
![[open id connect 2026-02-09 21.07.32.excalidraw]]![[open id connect 2026-02-09 21.08.50.excalidraw]]