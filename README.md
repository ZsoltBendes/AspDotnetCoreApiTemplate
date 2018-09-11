# AspDotnetCoreApiTemplate
[![Build Status](https://zsoltbendes.visualstudio.com/VSAPITemplate/_apis/build/status/ZsoltBendes.AspDotnetCoreApiTemplate)](https://zsoltbendes.visualstudio.com/VSAPITemplate/_build/latest?definitionId=7)
This is an empty template for creating new asp.net core api back end. It contains stuff I usually use in.
What I added to the empty template is:
- swagger
- AutoMapper
- Api versioning
- Sentry
Additionally I added an empty DB context.
## Swagger - aka OpenAPI
Swashbuckle allows to generate Swagger page from code and comments. This helps me to ensure I have clean api and don't have any route conflicts. You can test the apis with the swagger UI.
The config to reach the swagger ui is: `[app base url]/swagger`.
You can change the configuration in Startup.cs in region named `Swagger middleware`. You can also add some additional information to your swagger under `CreateInfoForApiVersion` method.

## AutoMapper
Why do mapping by hand? I use [AutoMapper](https://github.com/AutoMapper/AutoMapper). AutoMapper allows you to map your domain models to Dtos.
## Api Versioning
It is usefull for keeping backward compatibility.
In the ValuesController I added the sameple code to include api versioning. Just copy pase the class annotations.
</br>
`[ApiVersion("1.0")]`</br>
`[Produces("application/json")]`</br>
`[Route("api/v{version:apiVersion}/[controller]")]`</br>
`[ApiController]`</br>

## Sentry
The template contains a global exception handling for 500 error codes. Each time and exection occours that I did not catch the global exception handler will send the exception to Sentry.
[Check out Sentry on github.](https://github.com/getsentry/sentry)
The DSN can be configured from environment variable or in the appsettings.json file!
## DB Context
I included a db context under Data/ApplicationDbContext.cs. The template is configure to use MS SQL server. Change it as required. The 
service is configured in Startup.cs at line 40. The connections string can be configured from environment variable or in the appsettings.json file!
