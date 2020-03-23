---
title: Začínáme s Dockerem
description: Přečtěte si, jak přidat Docker do svých projektů ve Visual Studiu for Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 2c6bdd7d0b2c939ed9db9be962e89d9ee423e1d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984126"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Začínáme s Dockerem ve Visual Studiu pro Mac

S Visual Studio pro Mac můžete snadno vytvářet, ladit a spouštět kontejnerizované aplikace ASP.NET Core a publikovat je do Azure.

## <a name="prerequisites"></a>Požadavky

* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio pro Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalace a nastavení

Pro instalaci Dockeru si přečtěte a postupujte podle informací na [adrese Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Vytvoření ASP.NET základní webové aplikace a přidání podpory Dockeru

1. Vytvořte nové řešení tak, že přejdete na **Soubor > nové řešení**.
1. V části **.NET Core >** App ![zvolte šablonu webové **aplikace:** Vytvoření nové aplikace ASP.NET](media/docker-quickstart-1.png)
1. Vyberte cílovou architekturu. V tomto příkladu použijeme rozhraní .NET Core 2.2: ![Nastavení cílového rozhraní](media/docker-quickstart-2.png)
1. Zadejte podrobnosti projektu, například název (_DockerDemo_ v tomto příkladu). Vytvořený projekt obsahuje všechny základy, které potřebujete k vytvoření a spuštění webu ASP.NET Core.
1. V panelu řešení klikněte pravým tlačítkem myši na ![projekt DockerDemo a vyberte Přidat > Přidat podporu **Dockeru:** Přidat podporu dockeru](media/docker-quickstart-3.png)

Visual Studio pro Mac automaticky přidá nový projekt do vašeho řešení s názvem **docker-compose** a přidá **dockerfile** do vašeho stávajícího projektu.

![Generované soubory podpory dockeru](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Přehled souborů Dockeru

Dockerfile je recept pro vytvoření konečné image Dockeru. Odkazovat na [odkaz Dockerfile](https://docs.docker.com/engine/reference/builder/) pro pochopení příkazů v něm.

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

Předchozí *soubor Dockerfile* je založen na image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní bitové kopie vytvořením projektu a jeho přidáním do kontejneru.

> [!NOTE]
> Výchozí soubor Dockerfile vytvořený visual studio pro Mac zveřejňuje Port 80 pro přenos y HTTP. Chcete-li povolit `Expose 443` přenoshttps, přidejte do Dockerfile.

## <a name="debugging"></a>ladění

Vyberte `docker-compose` projekt jako projekt po spuštění a spusťte ladění **(Spustit > spustit ladění**). To bude sestavení, nasazení a spuštění projektu ASP.NET v kontejneru.

> [!TIP]
> Při prvním spuštění po instalaci aplikace Docker Desktop se při pokusu o ladění může zobrazit následující chyba:`Cannot start service dockerdemo: Mounts denied`
>
> Přidat `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` na kartu Sdílení souborů v Docker desktopu:
>
> ![Přidání složky NuGetFallbackFolder do sdílení souborů](media/docker-quickstart-5.png)

Po dokončení sestavení bude aplikace spuštěna v Safari:

![Výchozí projekt Dockeru spuštěný v Safari](media/docker-quickstart-6.png)

Všimněte si, že kontejner bude `http://localhost:32768` naslouchat na portu, například a tento port se může lišit.

Chcete-li zobrazit seznam spuštěných `docker ps` kontejnerů, použijte příkaz v terminálu.

Všimněte si portového relé na následujícím snímku obrazovky (v části **PORTY).** To ukazuje, že kontejner naslouchá na portu, který jsme viděli v Safari výše a předává požadavky internímu webovému serveru na portu 80 (jak je definováno v souboru Dockerfile). Z pohledu aplikace poslouchá na portu 80:

![Seznam kontejnerů Dockeru](media/docker-quickstart-7.png)
