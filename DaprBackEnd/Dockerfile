FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 8070

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["DaprBackEnd.csproj", "."]
RUN dotnet restore "DaprBackEnd.csproj"
COPY . .
WORKDIR "/src/"
RUN dotnet build "DaprBackEnd.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DaprBackEnd.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DaprBackEnd.dll"]