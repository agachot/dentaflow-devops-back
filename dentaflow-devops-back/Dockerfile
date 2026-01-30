# Étape 1 : build de l'application
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
# Copier les fichiers du projet
COPY . .
 
# Restaurer les dépendances
RUN dotnet restore
 
# Publier l'application
RUN dotnet publish -c Release -o /app/publish
 
# Étape 2 : image de runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
 
# Copier le résultat du build
COPY --from=build /app/publish .
 
# Port exposé par l'API
EXPOSE 8080
ENTRYPOINT ["dotnet", "dentaflow-devops-back.dll"]