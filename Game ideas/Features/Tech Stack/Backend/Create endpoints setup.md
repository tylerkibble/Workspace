`# Creating Endpoints for a .NET WebAPI with MongoDB This guide walks you through creating a .NET WebAPI project that interacts with MongoDB, focusing on setting up the project, designing the data model and MongoDB service, implementing CRUD operations, and testing the endpoints.  ## Prerequisites - A deployed and configured MongoDB Atlas cluster (M0 or higher). - .NET Core 6+. ## Step 1: Setting Up the Project 1. **Create a Web API Project**: Use the .NET Core CLI to create a new Web API project and install the MongoDB.Driver package.`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

bash dotnet new webapi -o MongoExample cd MongoExample dotnet add package MongoDB.Driver

``2. **Remove Boilerplate Files**: Delete any unnecessary files related to `WeatherForecast` or similar. ## Step 2: Designing the Data Model and MongoDB Service 1. **Create MongoDB Settings Class**: Define a `MongoDBSettings` class to hold connection details.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

csharp // Models/MongoDBSettings.cs namespace MongoExample.Models;

public class MongoDBSettings { public string ConnectionURI { get; set; } = null!; public string DatabaseName { get; set; } = null!; public string CollectionName { get; set; } = null!; }

``2. **Configure MongoDB Settings**: Add the MongoDB settings to the `appsettings.json` file.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

json "MongoDB": { "ConnectionURI": "YOUR_MONGODB_CONNECTION_STRING", "DatabaseName": "sample_mflix", "CollectionName": "playlist" }

``3. **Create MongoDB Service**: Implement the `MongoDBService` class to manage interactions with MongoDB.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

csharp // Services/MongoDBService.cs using MongoExample.Models; using Microsoft.Extensions.Options; using MongoDB.Driver; using MongoDB.Bson;

namespace MongoExample.Services;

public class MongoDBService { private readonly IMongoCollection<Playlist> _playlistCollection;

`public MongoDBService(IOptions<MongoDBSettings> mongoDBSettings) {     MongoClient client = new MongoClient(mongoDBSettings.Value.ConnectionURI);     IMongoDatabase database = client.GetDatabase(mongoDBSettings.Value.DatabaseName);     _playlistCollection = database.GetCollection<Playlist>(mongoDBSettings.Value.CollectionName); }`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

`// CRUD methods will be implemented later`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

}

``4. **Register MongoDB Service**: Configure the MongoDB service in the `Program.cs` file.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

csharp using MongoExample.Models; using MongoExample.Services;

var builder = WebApplication.CreateBuilder(args);

builder.Services.Configure<MongoDBSettings>(builder.Configuration.GetSection("MongoDB")); builder.Services.AddSingleton<MongoDBService>();

``## Step 3: Creating the Data Model 1. **Define Playlist Model**: Create a `Playlist` class to represent the structure of documents in the MongoDB collection.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

csharp // Models/Playlist.cs using MongoDB.Bson; using MongoDB.Bson.Serialization.Attributes; using System.Text.Json.Serialization;

namespace MongoExample.Models;

public class Playlist { [BsonId] [BsonRepresentation(BsonType.ObjectId)] public string? Id { get; set; }

`public string username { get; set; } = null!;`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

`[BsonElement("items")] [JsonPropertyName("items")] public List<string> movieIds { get; set; } = null!;`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

}

``## Step 4: Building CRUD Endpoints 1. **Create Playlist Controller**: Implement the `PlaylistController` to expose CRUD operations via HTTP endpoints.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

csharp // Controllers/PlaylistController.cs using System; using Microsoft.AspNetCore.Mvc; using MongoExample.Services; using MongoExample.Models;

namespace MongoExample.Controllers;

[Controller] [Route("api/[controller]")] public class PlaylistController: Controller { private readonly MongoDBService _mongoDBService;

`public PlaylistController(MongoDBService mongoDBService) {     _mongoDBService = mongoDBService; }`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

`// CRUD actions will be implemented here`

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

}

``2. **Implement CRUD Operations**:    - **Create**: Implement the `POST` method to create a new playlist.   - **Read**: Implement the `GET` method to retrieve playlists.   - **Update**: Implement the `PUT` method to update a playlist.   - **Delete**: Implement the `DELETE` method to delete a playlist. Each CRUD operation involves calling the corresponding method in the `MongoDBService` class, such as `InsertOneAsync`, `Find`, `UpdateOneAsync`, or `DeleteOneAsync`. ## Testing the Endpoints After implementing the CRUD operations, run the application and use tools like Postman or Swagger to test the endpoints. Start by testing the `POST` endpoint to add data, then use the generated ID to test the `GET`, `PUT`, and `DELETE` endpoints. This guide provides a structured approach to creating a .NET WebAPI project that interacts with MongoDB, including setting up the project, designing the data model and MongoDB service, implementing CRUD operations, and testing the endpoints.``

[

](https://www.phind.com/search?cache=zn5epjd53xh3ywfeohcgwnns)

