---
title: Visual Studio Tools for Docker s ASP.NET Core
author: ghogen
description: Naučte se používat nástroje sady Visual Studio 2019 a Docker for Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 0232b37d08901bcc04c9d66facfe6850a9852e88
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2019
ms.locfileid: "74485457"
---
Pomocí sady Visual Studio můžete snadno sestavovat, ladit a spouštět aplikace s podporou aplikací .NET, ASP.NET a ASP.NET Core a publikovat je do Azure Container Registry (ACR), Docker Hub, Azure App Service nebo vlastního registru kontejneru. V tomto článku publikujeme aplikaci ASP.NET Core do ACR.

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* [Vývojové nástroje .NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pro vývoj pomocí .net Core 2,2
* Pokud chcete publikovat Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalace a nastavení

Pro instalaci Docker si nejdřív přečtěte informace v části [Docker Desktop for Windows: co je potřeba před instalací](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)nástroje. Dále nainstalujte [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Přidání projektu do kontejneru Docker

1. Vytvořte nový projekt pomocí šablony **ASP.NET Core webové aplikace** .
1. Vyberte **Webová aplikace**a ujistěte se, že je zaškrtnuté políčko **Povolit podporu Docker** .

   ![Zaškrtávací políčko Povolit podporu Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Vyberte požadovaný typ kontejneru (Windows nebo Linux) a klikněte na **vytvořit**.

## <a name="dockerfile-overview"></a>Souboru Dockerfile – přehled

*Souboru Dockerfile*je v projektu vytvořen recept pro vytvoření finální image Docker. Porozumění příkazům, které jsou v něm, najdete v [referenčních informacích k souboru Dockerfile](https://docs.docker.com/engine/reference/builder/) :

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

Předchozí *souboru Dockerfile* vychází z image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru.

Když je zaškrtnuté políčko **Konfigurovat pro protokol HTTPS** v dialogovém okně Nový projekt, *souboru Dockerfile* zpřístupňuje dva porty. Pro přenosy HTTP se používá jeden port; druhý port se používá pro protokol HTTPS. Pokud políčko není zaškrtnuté, bude pro přenosy HTTP vystaven jeden port (80).

## <a name="debug"></a>Ladit

V rozevíracím seznamu ladění na panelu nástrojů vyberte **Docker** a spusťte ladění aplikace. Může se zobrazit zpráva s výzvou k důvěřování certifikátu. Chcete-li pokračovat, vyberte možnost důvěryhodného certifikátu.

V okně **výstup** se zobrazí možnost **nástroje kontejneru** , kde se zobrazují akce, které probíhají.

## <a name="containers-window"></a>Okno kontejnery

Pokud máte Visual Studio 2019 verze 16,4 nebo novější, můžete použít okno **kontejnery** k zobrazení spuštěných kontejnerů na počítači a také imagí, které máte k dispozici.

Otevřete okno **kontejnery** pomocí vyhledávacího pole v integrovaném vývojovém prostředí (stisknutím klávesy **CTRL**+**Q** ), zadejte `container`a zvolte okno **kontejnery** ze seznamu.

Okno **kontejnery** můžete připojit na vhodné místo, například pod editorem, přesunutím kolem a podle vodítek umístění okna.

V okně Najděte svůj kontejner a krok na každé kartě, abyste zobrazili proměnné prostředí, mapování portů, protokoly a systém souborů.

![Snímek okna kontejnerů](../../media/overview/vs-2019/container-tools-window.png)

Další informace najdete v tématu [zobrazení a diagnostika kontejnerů a imagí v aplikaci Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publikování imagí Docker

Jakmile se cyklus vývoje a ladění aplikace dokončí, můžete vytvořit provozní image aplikace.

1. Změňte rozevírací seznam konfigurace na **vydaná** a sestavte aplikaci.
1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **publikovat**.
1. V dialogovém okně Publikovat cíl vyberte kartu **Container Registry** .
1. Vyberte **vytvořit novou Azure Container Registry** a klikněte na **publikovat**.
1. Do pole **vytvořit nový Azure Container Registry**zadejte požadované hodnoty.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Formě** | Výběr předplatného | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, vyberte možnost **nové** .|
    | **[SKLADOVÉ](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio][0]

1. Klikněte na **vytvořit** .

   ![Snímek obrazovky znázorňující úspěšné publikování](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Další kroky

Kontejner teď můžete načíst z registru do libovolného hostitele, který podporuje spouštění imagí Docker, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
