# don't
- don't use exceptions to change the flow of a program as part of ordinary execution. Use exceptions to report and handle error conditions.
- exceptions shouldn't be returned as a return value or parameter instead of being thrown.
- don't throw [System.Exception](https://learn.microsoft.com/en-us/dotnet/api/system.exception), [System.SystemException](https://learn.microsoft.com/en-us/dotnet/api/system.systemexception), [System.NullReferenceException](https://learn.microsoft.com/en-us/dotnet/api/system.nullreferenceexception), or [System.IndexOutOfRangeException](https://learn.microsoft.com/en-us/dotnet/api/system.indexoutofrangeexception) intentionally from your own source code.
- don't create exceptions that can be thrown in debug mode but not release mode.

# do
## custom exceptions should define at least three constructors
```csharp
[Serializable]
public class InvalidDepartmentException : Exception
{
	public InvalidDepartmentException() : base() { }
	public InvalidDepartmentException(string message) : base(message) { }
	public InvalidDepartmentException(string message, Exception inner) : base(message, inner) { }
}
```
## use try/catch/finally blocks to recover from errors or release resources

### use try/catch/finally **if and only if** the block can recover from exception

**bad**
```csharp
public void Work()
{
	try
	{
		// throws exception
	}
	catch (Exception exception)
	{
		// do nothing meaningfull
	}
}
```

**good**
```csharp
public void Work()
{
	// throws exception
}
```

usually, when the execution ends after the catch block, it means that clock **can not** recover from the exception 

let the caller handle it, then

if you want to partially handle an exception, remember to rethrow correctly

```csharp
try
{
	// Try to access a resource.
}
catch (UnauthorizedAccessException e)
{
	LogError(e);
	throw;
}
```
### use try/catch/finally **only** around the code the can throw an exception

**bad**
```csharp
public async Task ExecuteAsync(CancellationToken cancellationToken)
{
	while(cancellationToken.IsCancellationRequested)
	{
		try
		{
			var settings = GetSettings();
			Worker.Execute(settings)
		}
		catch (ConnectionException exception)
		{
			// handle exception
		}
	}
}
```

**good**
```csharp
public async Task ExecuteAsync(CancellationToken cancellationToken)
{
	while(cancellationToken.IsCancellationRequested)
	{
		var settings = GetSettings();
		
		try
		{
			Worker.Execute(settings)
		}
		catch (ConnectionException exception)
		{
			// handle exception
		}
	}
}
```

because the block has no hope to recover if an exception is thrown while getting settings, and will keep failing indefinitely
### order the catch block from more derived to more generic

**bad**
```csharp
public void Connect()
{
    try
    {
        throw new System.Net.Sockets.SocketException();
    }
    catch (Exception ex)  // Base class caught first
    {
        // do something
    }
    catch (System.Net.Sockets.SocketException ex)  // Unreachable
    {
        // do something
    }
}
```

**good**
```csharp
public void Connect()
{
    try
    {
        throw new System.Net.Sockets.SocketException();
    }
    catch (System.Net.Sockets.SocketException ex)
    {
        // do something
    }
    catch (Exception ex)
    {
        // do something
    }
}
```


### clean up resource

**bad**
```csharp
public void Write(string filePath)
{
    StreamWriter writer = null;

    try
    {
        writer = new StreamWriter(filePath);
        writer.WriteLine("Important data...");

        // Simulate an exception
        throw new Exception("Unexpected error");
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error: {ex.Message}");
    }

    // No cleanup! The file handle may remain open
}
```

**best**
```csharp
public void Write(string filePath)
{
    try
    {
        using (StreamWriter writer = new StreamWriter(filePath))
        {
            writer.WriteLine("Important data...");
            throw new Exception("Unexpected error");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error: {ex.Message}");
    }
}
```

**good**
```csharp
public void Write(string filePath)
{
    StreamWriter writer = null;

    try
    {
        writer = new StreamWriter(filePath);
        writer.WriteLine("Important data...");

        // Simulate an exception
        throw new Exception("Unexpected error");
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error: {ex.Message}");
    }
    finally
    {
        if (writer != null)
        {
            writer.Close(); // Proper cleanup
            Console.WriteLine("File stream closed.");
        }
    }
}
```

because unrelease **file locks** could prevent other processes from accessing the file
## handle common conditions to avoid exceptions

**bad**
```csharp
try
{
	conn.Close();
}
catch (InvalidOperationException ex)
{
	// do something
}
```

**good**
```csharp
if (conn.State != ConnectionState.Closed)
{
	conn.Close();
}
```

another example

**bad**
```csharp
try
{
	int.Parse()
}
catch (OverflowException ex)
{
	// do something
}
```

**good**
```csharp
int.TryParse()
```

because handling exception has overhead
## catch cancellation and asynchronous exceptions
review [Handle asynchronous exceptions](https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/#handle-asynchronous-exceptions)
review [Exceptions in task-returning methods](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/creating-and-throwing-exceptions#exceptions-in-task-returning-methods)


[continue later](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions)