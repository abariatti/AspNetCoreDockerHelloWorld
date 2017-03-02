#ASP.Net Core HelloWorld with docker support

Based on the following tutorial: https://stormpath.com/blog/tutorial-deploy-asp-net-core-on-linux-with-docker

## Step 1 - Create dotnet core project
```BASH
mkdir AspNetCoreHelloWorld
cd AspNetCoreHelloWorld
dotnet new -t web
```

Make sure everything is working!
```BASH
dotnet restore
dotnet run
```

## Step 2 - Build dockerfile for ASP.NET Core

```Docker
FROM microsoft/dotnet:latest
COPY . /app
WORKDIR /app
 
RUN ["dotnet", "restore"]
RUN ["dotnet", "build"]
 
EXPOSE 5000/tcp
ENV ASPNETCORE_URLS http://*:5000
 
ENTRYPOINT ["dotnet", "run"]
```

Here’s what each of these instructions does:

FROM tells Docker that you want to base your image on the existing image called microsoft/dotnet:latest. This image already contains all the dependencies for running .NET Core on Linux, so you don’t have to worry about setting those up.
COPY and WORKDIR copy the current directory’s contents into a new directory inside the container called /app, and set that to the the working directory for the subsequent instructions.
RUN executes dotnet restore and dotnet build, which restores the packages needed to run the ASP.NET Core application and compiles the project.
EXPOSE tells Docker to expose port 5000 (the default port for ASP.NET) on the container.
ENV sets the environment variable ASPNETCORE_URLS in the container. This will ensure that ASP.NET Core binds to the correct port and address.
ENTRYPOINT specifies the command to execute when the container starts up. In this case, it’s dotnet run.
