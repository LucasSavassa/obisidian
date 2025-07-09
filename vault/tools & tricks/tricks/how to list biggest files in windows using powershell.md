``` powershell
Get-ChildItem -Path C:\ -Recurse | Sort-Object Length -Descending | Select-Object FullName, Length -First 20
```
