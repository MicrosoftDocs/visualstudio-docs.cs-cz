---
title: Nástroje Visual Studia pro Docker s ASP.NET
author: ghogen
description: Přečtěte si, jak používat nástroje Visual Studio 2019 a Docker pro Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 3869cf025b4ed0e744a7fea929aac38acb7dd816
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922997"
---
Pomocí Visual Studia můžete snadno vytvářet, ladit a spouštět kontejnerizované aplikace .NET, ASP.NET a ASP.NET Core a publikovat je do registru kontejnerů Azure (ACR), Docker Hubu, služby Azure App Service nebo vlastního registru kontejnerů. V tomto článku publikujeme aplikaci ASP.NET Core do ACR.

## <a name="prerequisites"></a>Požadavky

* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core**
* [Nástroje pro vývoj jádra rozhraní .NET](https://dotnet.microsoft.com/download/dotnet-core/)
* Chcete-li publikovat do registru kontejnerů Azure, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Dockeru nejprve zkontrolujte informace na [ploše Dockeru pro Windows: Co je třeba vědět před instalací](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Dále nainstalujte [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Přidání projektu do kontejneru Dockeru

1. Vytvořte nový projekt pomocí šablony **ASP.NET základní webové aplikace** nebo pokud chcete použít rozhraní .NET Framework místo .NET Core, zvolte ASP.NET Web Application **(.NET Framework).**
1. Vyberte **Webová aplikace**a ujistěte se, že je zaškrtnuté políčko **Povolit podporu dockeru.**

   ![Zaškrtávací políčko Povolit podporu Dockeru](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   Snímek obrazovky zobrazuje jádro .NET; Pokud používáte rozhraní .NET Framework, vypadá to trochu jinak.

1. Vyberte požadovaný typ kontejneru (Windows nebo Linux) a klepněte na **tlačítko Vytvořit**.

## <a name="dockerfile-overview"></a>Přehled souborů Dockeru

*Dockerfile*, recept pro vytvoření konečné image Dockeru, je vytvořen v projektu. Naleznete [na Dockerfile odkaz](https://docs.docker.com/engine/reference/builder/) pro pochopení příkazů v něm.:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Předchozí *soubor Dockerfile* je založen na image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní bitové kopie vytvořením projektu a jeho přidáním do kontejneru. Pokud používáte rozhraní .NET Framework, základní bitová kopie se bude lišit.

Když je zaškrtnuto políčko **Konfigurovat pro protokol HTTPS** nového dialogového okna projektu, *dockerfile* zpřístupní dva porty. Jeden port se používá pro přenosy HTTP; druhý port se používá pro protokol HTTPS. Pokud políčko není zaškrtnuto, jeden port (80) je vystaven pro přenosy HTTP.

## <a name="debug"></a>Ladění

Vyberte **Docker** z rozevíracího okna ladění na panelu nástrojů a začněte ladit aplikaci. Může se zobrazit zpráva s výzvou k důvěře certifikátu. zvolte důvěřovat certifikátu, aby mohl pokračovat.

Možnost **Nástroje kontejneru** v okně **Výstup** ukazuje, jaké akce probíhají. Poprvé může chvíli trvat, než se základní obrázek stáhne, ale při následných spuštěních je mnohem rychlejší.

## <a name="containers-window"></a>Okno kontejnerů

Pokud máte Visual Studio 2019 verze 16.4 nebo novější, můžete použít okno **Kontejnery** k zobrazení spuštěné kontejnery na vašem počítači, stejně jako obrázky, které máte k dispozici.

Otevřete okno **Kontejnery** pomocí vyhledávacího pole v ide (stisknutím `container` **ctrl**+**q** použít), zadejte a vyberte **okno Kontejnery** ze seznamu.

Okno **Kontejnery** můžete připojit na vhodnémísto, například pod editorem, přesunutím a podle vodítek umístění okna.

V okně najděte kontejner a krokujte každou kartu a zobrazte proměnné prostředí, mapování portů, protokoly a souborový systém.

![Snímek obrazovky s oknem Kontejnery](../../media/overview/vs-2019/container-tools-window.png)

Další informace naleznete v [tématu Zobrazení a diagnostika kontejnerů a obrázků v sadě Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publikovat imitace Dockeru

Po dokončení cyklu vývoje a ladění aplikace můžete vytvořit produkční bitovou kopii aplikace.

1. Změňte rozbalovací verzi konfigurace na **Uvolnění** a vytvořte aplikaci.
1. Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a zvolte **Publikovat**.
1. V dialogovém okně publikovat cíl vyberte kartu **Registr kontejneru.**
1. Zvolte **Vytvořit nový registr kontejnerů Azure** a klepněte na **publikovat**.
1. Vyplňte požadované hodnoty v **registru vytvořit nový kontejner Azure**.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jednoznačně identifikuje registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve kterém chcete vytvořit registr kontejneru. Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění v blízkosti vás | Zvolte umístění v [oblasti](https://azure.microsoft.com/regions/) ve vašem okolí nebo v blízkosti jiných služeb, které budou používat registr kontejnerů. |

    ![Dialogové okno Vytvořit registr kontejnerů Azure v Sadě Visual Studio][0]

1. Klikněte na **Vytvořit.**

   ![Snímek obrazovky s úspěšným publikováním](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Další kroky

Nyní můžete vytáhnout kontejner z registru na libovolného hostitele schopného spouštět ibi Dockeru, například [instance kontejneru Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
