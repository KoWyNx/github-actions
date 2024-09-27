FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src/worker/

COPY src/Worker/Worker.csproj ./
RUN dotnet restore

COPY src/Worker/. ./
RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Worker.dll"]
