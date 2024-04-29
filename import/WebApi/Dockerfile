FROM --platform=$BUILDPLATFORM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ./import/WebApi/ .
RUN mkdir /app
RUN dotnet publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
EXPOSE 8080
WORKDIR /app
COPY --from=build /src/bin/Release/net8.0/publish .
# USER $APP_UID
ENTRYPOINT [ "dotnet", "MicroserviceApi.WebApi.dll" ]