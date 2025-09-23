# migration
[getting started](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#getting-started)
migration keeps a database in sync with model defined in code
![[asp.net.core.identity 2025-09-22 09.05.36.excalidraw]]

entity framework keeps track of model changes
it compares current model to last snapshot
when changes exists, it can produce a .migration
.migration can be shared
![[asp.net.core.identity 2025-09-23 17.04.08.excalidraw]]