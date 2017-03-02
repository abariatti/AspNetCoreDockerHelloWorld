#Asp.Net Core HelloWorld with docker support

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

## Step 2 - 