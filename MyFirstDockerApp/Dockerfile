#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.
#
#FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
#WORKDIR /app
#EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app
COPY *csproj ./
RUN dotnet restore
COPY . ./

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:7.0 as runtime
WORKDIR /app
COPY --from=build /app/out ./

EXPOSE 80

ENTRYPOINT ["dotnet", "MyFirstDockerApp.dll"]

#
#FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
#WORKDIR /src
#COPY ["MyFirstDockerApp/MyFirstDockerApp.csproj", "MyFirstDockerApp/"]
#RUN ls -la
#RUN dotnet restore "MyFirstDockerApp/MyFirstDockerApp.csproj"
#COPY . .
#WORKDIR "/src/MyFirstDockerApp"
#RUN dotnet build "MyFirstDockerApp.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "MyFirstDockerApp.csproj" -c Release -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "MyFirstDockerApp.dll"]