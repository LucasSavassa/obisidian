- there are two types of users: customer and admin
- customer accounts are typically created through self-service sign-up
- customer accounts have very limited permissions by default
- admin accounts will typically be assigned to workforce members
# integrate
- read [planning for customer identity and access management](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-planning-your-solution)
- step 1: create tenant
- step 2: register app
- step 3: create and integrate sign-in flow
- step 4: customize and secure sign-in flow
# authentication flow
- mapping an app to an user flow creates endpoints
![[azure.microsoft entra.external 2026-01-19 21.06.54.excalidraw]]
- this endpoints controls sign-in experience
- when user attempts to access a protected resource, it is redirected to the sign-in user flow
![[azure.microsoft entra.external 2026-01-19 20.58.05.excalidraw]]
- if it is signing in for the first time, it gets redirected to the sign-up experience
- the sign-up experience prompts user for default attributes + custom attributes
![[azure.microsoft entra.external 2026-01-19 21.09.29.excalidraw]]
- when sign-in is completed, an access token is delivered.
- when sign-up is completed, an user is created in the directory