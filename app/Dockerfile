FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY manaliassignment/*.csproj .
RUN dotnet restore

# Copy everything else and build website
COPY manaliassignment/. .
RUN dotnet publish -c release -o /WebApp --no-restore

# Final stage / image
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /WebApp
COPY --from=build /WebApp ./
ENTRYPOINT ["dotnet", "ManaliAssignment.dll"]
