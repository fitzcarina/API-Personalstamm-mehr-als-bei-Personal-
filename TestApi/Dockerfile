#Get base SDK Image from Microsoft

#FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env
#WORKDIR /app


#COPY * .csproj ./

#RUN
#Copy the project files and build our release
#COPY . ./
#RUN dotnet publish -c Release -o out
#Generate runtime image
#FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
#WORKDIR /app
#EXPOSE 80
#COPY --from=build-env /app/out .
#ENTRYPOINT [ "dotnet", "DockerAPI.dll" ]
FROM mcr.microsoft.com/dotnet/sdk:6.0-focal AS build
WORKDIR /source



COPY . .
RUN dotnet restore "./API 13.07.2022/TestApi.csproj" --disable-parallel

RUN dotnet publish "./API 13.07.2022/TestApi.csproj" -c release -o /app --no-restore
FROM mcr.microsoft.com/dotnet/aspnet:6.0-focal
WORKDIR /app
COPY --from=build /app ./
EXPOSE 5000
ENTRYPOINT ["dotnet", "TestApi.dll"]