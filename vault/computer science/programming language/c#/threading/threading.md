[reference](https://learn.microsoft.com/en-us/dotnet/standard/threading/threads-and-threading)
# concept
- a computer runs processes
- processes have isolated code, isolated memory, isolated context
- threads represent groups of "independent" tasks (in a process)
- threads share some data, but also have isolated assets
- if a computer has two cpus, each could run a thread concurrently
v1![[csharp.threading 2025-12-12 10.52.45.excalidraw]]
# dotnet
- .NET always starts a program with a single thread

# example
![[csharp.threading 2025-12-12 11.21.15.excalidraw]]