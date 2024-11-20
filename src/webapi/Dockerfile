# Use the official .NET Core SDK image to build the application
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the .csproj file and restore any dependencies
COPY *.csproj ./
RUN dotnet restore

# Copy the rest of the application code
COPY . ./

# Build the application
RUN dotnet publish -c Release -o out

# Use the official .NET Core runtime image to run the application
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base

# Set the working directory inside the container
WORKDIR /app

# Copy the built application from the build stage
COPY --from=build /app/out .

# Expose the port the application runs on
EXPOSE 8080

# Set the entry point for the application
ENTRYPOINT ["dotnet", "webapi.dll"]