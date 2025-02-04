
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
# Copia o arquivo de projeto e restaura as dependências
COPY *.csproj ./
RUN dotnet restore
# Copia o restante do código e compila a aplicação
COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .

# Define o comando de inicialização da aplicação
ENTRYPOINT ["dotnet", "ItemService.dll"]
