FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 21153
EXPOSE 44333

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
WORKDIR /src
COPY . .
RUN dotnet restore


FROM build AS publish
RUN dotnet publish -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "TokenServiceApi.dll"]
