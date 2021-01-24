# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /app

# Copy csproj and restore as distinct   
COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c release -o out

# Build
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "CatalogAPI.dll"]