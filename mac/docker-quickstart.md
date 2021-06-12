---
title: Začínáme s Dockerem
description: Zjistěte, jak přidat Docker do projektů v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 4ddb15c8bc5bf90663c5431d2379af61b43e73a6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043091"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Začínáme s Dockerem v Visual Studio pro Mac

Díky Visual Studio pro Mac můžete snadno sestavovat, ladit a spouštět kontejnerizované aplikace ASP.NET Core a publikovat je do Azure.

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio pro Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Dockeru si prohlédněte informace v instalaci [Docker Desktopu](https://docs.docker.com/docker-for-mac/install/)pro Mac a postupujte podle těchto informací.

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Vytvoření webové ASP.NET Core a přidání podpory Dockeru

1. Vytvořte nové řešení tak, že v **souboru > Nové řešení.**
1. V **části .NET Core > App** zvolte šablonu **Webová** ![ aplikace: Vytvoření nové ASP.NET aplikace](media/docker-quickstart-1.png)
1. Vyberte cílovou rozhraní. V tomto příkladu použijeme .NET Core 2.2: ![ Nastavení cílové architektury](media/docker-quickstart-2.png)
1. Zadejte podrobnosti projektu, například name _(v tomto příkladu DockerDemo)._ Vytvořený projekt obsahuje všechny základy, které potřebujete k sestavení a spuštění ASP.NET Core.
1. V okně Řešení klikněte pravým tlačítkem na projekt DockerDemo a vyberte **Add > Docker Support**: Add docker support (Přidat podporu Dockeru): Add docker support (Přidat podporu ![ Dockeru).](media/docker-quickstart-3.png)

Visual Studio pro Mac do vašeho řešení automaticky přidá nový projekt s názvem **docker-compose** a do existujícího projektu přidá soubor **Dockerfile.**

![Vygenerované podpůrné soubory Dockeru](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Přehled souboru Dockerfile

Recept na vytvoření konečné image Dockerfile je Dockerfile. Informace o příkazech v souboru [Dockerfile](https://docs.docker.com/engine/reference/builder/) najdete v referenčních informacích.

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore "DockerDemo/DockerDemo.csproj"
COPY . .
WORKDIR "/src/DockerDemo"
RUN dotnet build "DockerDemo.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DockerDemo.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Předchozí soubor *Dockerfile* vychází z image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru.

> [!NOTE]
> Výchozí soubor Dockerfile vytvořený Visual Studio pro Mac zpřístupňuje port 80 pro provoz HTTP. Pokud chcete povolit provoz HTTPS, `Expose 443` přidejte do souboru Dockerfile.

## <a name="debugging"></a>Ladění

Vyberte projekt `docker-compose` jako spouštěný projekt a spusťte ladění ( Spustit > Spustit **ladění**). Tím sestavíte, nasadíte a spustíte ASP.NET projektu v kontejneru.

> [!TIP]
> Při prvním spuštění po instalaci Docker Desktopu se může při pokusu o ladění zobrazit následující chyba: `Cannot start service dockerdemo: Mounts denied`
>
> Na `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` kartě Sdílení souborů v Docker Desktopu přidejte :
>
> ![Přidání složky NuGetFallbackFolder do sdílení souborů](media/docker-quickstart-5.png)

Po dokončení sestavení se aplikace spustí v prohlížeči Safari:

![Výchozí projekt Dockeru spuštěný v Safari](media/docker-quickstart-6.png)

Všimněte si, že kontejner bude například naslouchat na portu a tento `http://localhost:32768` port se může lišit.

Pokud chcete zobrazit seznam spuštěných kontejnerů, použijte `docker ps` příkaz v Terminálu.

Poznamenejte si přenos portů na následujícím snímku obrazovky (v části **PORTY).** To ukazuje, že kontejner naslouchá na portu, který jsme viděli výše v Safari, a předává požadavky internímu webovému serveru na portu 80 (jak je definováno v souboru Dockerfile). Z pohledu aplikace naslouchá na portu 80:

![Seznam kontejnerů Dockeru](media/docker-quickstart-7.png)
