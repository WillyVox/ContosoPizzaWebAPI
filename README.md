## ContosoPizza

### mkdir ContosoPizza

### $ dotnet new webapi -controllers -f net8.0
    This command creates the files for a basic web API project that uses controllers, along with a C# project file named ContosoPizza.csproj that returns a list of weather forecasts. If you get an error, ensure that you have the .NET 8 SDK installed.

### 
    You should now have access to these files and directories:

    -| Controllers
    -| obj
    -| Properties
    -| appsettings.Development.json
    -| appsettings.json
    -| ContosoPizza.csproj
    -| ContosoPizza.http
    -| Program.cs
    -| WeatherForecast.cs
Examine the following files and directories:

Name	              Description
Controllers/	      Contains classes with public methods exposed as HTTP endpoints.
Program.cs	          Configures services and the app's HTTP request pipeline, and contains the app's managed entry point.
ContosoPizza.csproj	  Contains configuration metadata for the project.
ContosoPizza.http	  Contains configuration to test REST APIs directly from Visual Studio Code.
