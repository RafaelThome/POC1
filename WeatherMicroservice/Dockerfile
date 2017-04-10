FROM microsoft/dotnet:1.1-sdk-msbuild

WORKDIR /app

# copy csproj
COPY WeatherMicroservice.csproj .

ENV ASPNETCORE_URLS http://+:5000
ENV ASPNETCORE_ENVIRONMENT="Development"
EXPOSE 80


# Restore NuGet packages
RUN ["dotnet", "restore"]

# Build the app
RUN ["dotnet", "build"]

# copy and build everything else
COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out

ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
