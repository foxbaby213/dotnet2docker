FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 5000

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
#COPY ["dotnet2docker/dotnet2docker.csproj", "dotnet2docker/"]
RUN dotnet restore "/dotnet2docker.csproj"
COPY . .
WORKDIR "/src/dotnet2docker"
RUN dotnet build "dotnet2docker.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "dotnet2docker.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "dotnet2docker.dll"]