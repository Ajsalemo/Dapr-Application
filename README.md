# Dapr-Application
Testing Dapr out with a simple front-end and back-end service.

`DaprFrontEnd` - ASP .NET Core application that acts as the 'front end'. Uses the `Dapr.Client` package to call to the `DaprBackEnd` service.
`DaprBackEnd` - ASP . NET Core application that acts an API providing randomized generic weather data.

This project can be started by running `docker-compose up`.
