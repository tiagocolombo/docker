FROM microsoft/aspnetcore:1.1 AS base
WORKDIR /release
EXPOSE 5000/tcp
ENV ASPNETCORE_URLS http://*:5000

FROM microsoft/dotnet:2.0-sdk AS build
WORKDIR /application
COPY *.csproj .
COPY . .

RUN dotnet clean
RUN dotnet restore -nowarn:msb3202,nu1503
RUN dotnet build -c Release -o /release

FROM build AS publish
WORKDIR /application
RUN dotnet publish -c Release -o /release

FROM base AS final
WORKDIR /release
COPY --from=publish /release .
ENTRYPOINT ["dotnet", "Application.dll"]