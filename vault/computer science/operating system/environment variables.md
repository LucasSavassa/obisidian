# summary
- environments variables is a global dictionary embedded in every operating system
- { key } -> { value }
- value.type = plain text
# how to
## windows
### set
#### temporary
```powershell
$env:{ key } = { value }
```
#### user permanent
```powershell
[System.Environment]::SetEnvironmentVariable(
	"{ key }", "{ value }", "User"
)
```
#### global permanent
```powershell
[System.Environment]::SetEnvironmentVariable(
	"{ key }", "{ value }", "Machine"
)
```
### read
#### temporary
```powershell
$env:{ key }
```
#### user permanent
```powershell
[System.Environment]::GetEnvironmentVariable("{ key }", "User")
```
#### global permanent
```powershell
[System.Environment]::GetEnvironmentVariable("{ key }", "Machine")
```