FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 5000

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /app
COPY . /app
RUN dotnet restore "app/dotnet2docker.csproj"
COPY . .
WORKDIR "/app/dotnet2docker"
RUN dotnet build "dotnet2docker.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "dotnet2docker.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "dotnet2docker.dll"]