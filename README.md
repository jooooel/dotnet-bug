# dotnet-bug

Using .NET 7 running `dotnet test -p:BuildInParallel=false dirs.proj` will fail with `error MSB1011: Specify which project or solution file to use because this folder contains more than one project or solution file`. Running `dotnet test dirs.proj` works. For .NET 6, both work.

Running `dotnet msbuild -p:BuildInParallel=false dirs.proj` with .NET 7 works as well.

Forcing the usage of .NET 6 using a `global.json` like this also works:
```
{
  "sdk": {
    "version": "6.0.403",
    "rollForward": "latestMinor"
  }
}
```
