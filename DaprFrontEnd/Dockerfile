FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 8090

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["DaprFrontEnd.csproj", "."]
RUN dotnet restore "DaprFrontEnd.csproj"
COPY . .
WORKDIR "/src/"
RUN dotnet build "DaprFrontEnd.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DaprFrontEnd.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .

ENTRYPOINT ["dotnet", "DaprFrontEnd.dll"]