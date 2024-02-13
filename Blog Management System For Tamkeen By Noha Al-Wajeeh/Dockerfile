#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["Blog Management System For Tamkeen By Noha Al-Wajeeh/Blog Management System For Tamkeen By Noha Al-Wajeeh.csproj", "Blog Management System For Tamkeen By Noha Al-Wajeeh/"]
RUN dotnet restore "Blog Management System For Tamkeen By Noha Al-Wajeeh/Blog Management System For Tamkeen By Noha Al-Wajeeh.csproj"
COPY . .
WORKDIR "/src/Blog Management System For Tamkeen By Noha Al-Wajeeh"
RUN dotnet build "Blog Management System For Tamkeen By Noha Al-Wajeeh.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Blog Management System For Tamkeen By Noha Al-Wajeeh.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Blog Management System For Tamkeen By Noha Al-Wajeeh.dll"]