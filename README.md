# Memo on the creation of a JWT token based auth in .NET 6

## Visual Studio project type: ASP .NET Core Web API.
## Nuget:
	- Microsoft.AspNetCore.Authentication.JwtBearer,
	(- Microsoft.EntityFrameworkCore.SqlServer,
	- Microsoft.EntityFrameworkCore.Tools, 
	- Microsoft.AspNetCore.Identity.EntityFrameworkCore)
##Into appsettings.json:
	"JWT": {
		"Key": "kljuc",
		"Issuer": "izdavac",
		"Audience": ""42069"
	  }
## Configuring a strongly typed settings object as a dependency injection based on appsettings.json:
	- Define the object inside of root of appsettings.json;
		e.g. "JWT": {
				"Key": "kljuc",
				"Issuer": "izdavac",
				"Audience": ""42069"
			  }
	- Create a class with the name of the object as the class name and the attributes as the variables.
	- In Program.cs: services.Configure<JWT>(builder.Configuration.GetSection("JWT"));
	- Where you want to utilize the settings object:
		private readonly JWT _jwt;
		public UserService(IOptions<JWT> jwt)
		{
		   _jwt = jwt.Value;
		}
