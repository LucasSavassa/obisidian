# words
- anomaly?
- cost allocation engine
- tag inheritance
- split shared costs
- azure advisor
- cost alert
- budget
- scheduled alert
- storage account
- scheduled exports
# summary
- usage and purchase quantity are sent by microsoft products to the pipeline.
- discount is applied based on price sheet and the final rated usage is calculated based on pricing model (e.g. block pricing)
- purchase quantity is measured differently than pricing quantity
- finally, credits are applied and invoice is generated

![[azure.cost management 2026-01-15 19.18.59.excalidraw]]
# calendar
- process starts 72 hours after end of billing period (usually end of month)
- therefore, invoices are usually available at 4th day 
# tools
- there is billing and cost management
- cost management is withing billing but not only
- cost management is also available in subscription, resource groups, ... , and independently
## billing
- for invoices and payment options
- include taxes, credits, and some edge-case costs
## cost management
### budgets
- exist at tenant level, subscription level and resource group level
- can notify robots to take automated action
### anomaly
- anomaly is a discontinuation in a linear curve of cost
- either a spike or a dip
- can trigger notification
### scheduled alert
- periodically send cost data
# actions
## organize cost
### billing profiles and invoice sections
![[azure.cost management 2026-01-15 20.00.58.excalidraw]]
### departments and enrollment accounts
...
### management groups
...
### subscriptions and resource groups
...
### resource tags
...

## allocate cost
### tag inheritance
- you can assign tags to subscriptions that are further inherited by child resource and can be operated upon during invoice building
### allocation
- once subscriptions, resource groups and tags are configured, it's possible to allocate costs from one subscriptions to another
