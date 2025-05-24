## ContosoPizza

### mkdir ContosoPizza

### $ dotnet new webapi -controllers -f net8.0
    This command creates the files for a basic web API project that uses controllers, along with a C# project file named ContosoPizza.csproj that returns a list of weather forecasts. If you get an error, ensure that you have the .NET 8 SDK installed.

### Code structure
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

### Run app
    $ dotnet run

### Test App
    http://localhost:5045/weatherforecast

    http://localhost:5045/swagger/v1/swagger.json

### Optional: Explore APIs with Command Line HTTP REPL
    1. Open a new integrated terminal from Visual Studio Code by selecting Terminal > New Terminal from the main menu, then run the following command:
        $ dotnet tool install -g Microsoft.dotnet-httprepl
    2. Connect to the web API by running the following command:
        $ httprepl http://localhost:5045
    Alternatively, run the following command at any time while HttpRepl is running:
        $ connect http://localhost:5045
    3. Explore available endpoints by running the following command:
        $ ls
    4. Go to the WeatherForecast endpoint by running the following command:
        $ cd WeatherForecast
        $ get
        $ exit

### Add a data store
    Create a pizza model
    1. Run the following command to create a Models folder:
        $ mkdir Models
    2. Add the following code to Models/Pizza.cs and save your changes. This class defines a pizza.

### Add a data service
    1. Run the following command to create a Services folder:
        $ mkdir Services
    2. Add the following code to Services/PizzaService.cs and save your changes. This code creates an in-memory pizza data service.
### Build the web API project
    $ dotnet build

### Add a controller
    A controller is a public class with one or more public methods known as actions. By convention, a controller is placed in the project root's Controllers directory. The actions are exposed as HTTP endpoints inside the web API controller.

    Create a controller
        Select the Controllers folder in Visual Studio Code and add a new file called PizzaController.cs.

    1. Get all pizzas
        [HttpGet]
        public ActionResult<List<Pizza>> GetAll() => PizzaService.GetAll();
    2. Retrieve a single pizza
        [HttpGet("{id}")]
        public ActionResult<Pizza> Get(int id)
        {
            var pizza = PizzaService.Get(id);

            if(pizza == null)
                return NotFound();

            return pizza;
        }
    3. Build and run the new controller
        Build and start the web API by running the following command:
        $ dotnet run
    4. Test the controller with an Http file
        - Open ContosoPizza.http
        - Add a new GET to call the Pizza endpoint under the ### seperator:
            GET {{ContosoPizza_HostAddress}}/pizza/
            Accept: application/json
        - Test $ http://localhost:5045/pizza
    6. To query for a single pizza, you can make another GET request, but pass in an id parameter by using the following command:
        GET {{ContosoPizza_HostAddress}}/pizza/1
        Accept: application/json
        - Test: $ http://localhost:5045/pizza/1
    7. Optional: Test the controller with Command Line HTTP Read-Eval-Print Loop (REPL) 
        [https://learn.microsoft.com/en-gb/training/modules/build-web-api-aspnet-core/6-exercise-add-controller]
        