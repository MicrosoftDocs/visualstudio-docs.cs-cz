---
title: Začínáme s Docker
description: Naučte se, jak přidat Docker do vašich projektů v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 2c6bdd7d0b2c939ed9db9be962e89d9ee423e1d4
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984126"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Začínáme s Docker v Visual Studio pro Mac

Pomocí Visual Studio pro Mac můžete snadno sestavovat, ladit a spouštět ASP.NET Core aplikace a publikovat je v Azure.

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Docker zkontrolujte a použijte informace v části [instalace Docker Desktop pro Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Vytvoření webové aplikace ASP.NET Core a přidání podpory Docker

1. Nové řešení můžete vytvořit tak, že na **soubor > nové řešení**.
1. V části **aplikace .NET Core >** vyberte šablonu **webové aplikace** : ![vytvoření nové aplikace ASP.NET](media/docker-quickstart-1.png)
1. Vyberte cílovou architekturu. V tomto příkladu použijeme .NET Core 2,2: ![nastavit cílovou architekturu](media/docker-quickstart-2.png)
1. V tomto příkladu zadejte podrobnosti projektu, například název (_DockerDemo_ ). Vytvořený projekt obsahuje všechny základy, které potřebujete k vytvoření a spuštění webu ASP.NET Core.
1. V Oblast řešení klikněte pravým tlačítkem na projekt DockerDemo a vyberte **přidat > přidat podporu Docker**: ![přidat podporu docker](media/docker-quickstart-3.png)

Visual Studio pro Mac automaticky přidá nový projekt do vašeho řešení s názvem **Docker-** **souboru Dockerfile** a přidá do existujícího projektu.

![Vygenerované soubory podpory Docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Souboru Dockerfile – přehled

Souboru Dockerfile je recept pro vytvoření finální image Docker. Porozumění příkazům, které jsou v něm, najdete v [referenčních informacích k souboru Dockerfile](https://docs.docker.com/engine/reference/builder/) .

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Předchozí *souboru Dockerfile* vychází z image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru.

> [!NOTE]
> Výchozí souboru Dockerfile vytvořený pomocí Visual Studio pro Mac zveřejňuje port 80 pro přenosy HTTP. Pokud chcete povolit přenosy přes protokol HTTPS, přidejte `Expose 443` do souboru Dockerfile.

## <a name="debugging"></a>Ladění

Vyberte projekt `docker-compose` jako spouštěný projekt a spusťte ladění (**Spustit ladění > spustit ladění**). Tím se sestaví, nasadí a spustí projekt ASP.NET v kontejneru.

> [!TIP]
> Při prvním spuštění po instalaci Docker desktopu se při pokusu o ladění může zobrazit následující chyba: `Cannot start service dockerdemo: Mounts denied`
>
> Přidejte `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` na kartu Sdílení souborů v Docker desktopu:
>
> ![Přidání složky NuGetFallbackFolder do sdílení souborů](media/docker-quickstart-5.png)

Po dokončení sestavení se aplikace spustí v Safari:

![Výchozí projekt Docker běžící v Safari](media/docker-quickstart-6.png)

Všimněte si, že kontejner naslouchá na portu, `http://localhost:32768` například a tento port se může lišit.

Pokud chcete zobrazit seznam spuštěných kontejnerů, použijte příkaz `docker ps` v terminálu.

Poznamenejte si port Relay na snímku obrazovky dole (v části **porty**). To ukazuje, že kontejner naslouchá na portu, který jsme viděli v Safari výše, a přenáší požadavky na interní WebServer na portu 80 (jak je definováno v souboru Dockerfile). Z perspektivy aplikace naslouchá na portu 80:

![Seznam kontejnerů Docker](media/docker-quickstart-7.png)
