---
title: Visual Studio Tools for Docker s ASP.NET
author: ghogen
description: Naučte se používat nástroje sady Visual Studio 2019 a Docker for Windows
ms.author: ghogen
ms.date: 02/22/2021
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 35beb1bb67dbfe4d0d1707c499b605f6ff698956
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2021
ms.locfileid: "112907999"
---
Pomocí sady Visual Studio můžete snadno sestavovat, ladit a spouštět aplikace s podporou aplikací .NET, ASP.NET a ASP.NET Core a publikovat je do Azure Container Registry (ACR), Docker Hub, Azure App Service nebo vlastního registru kontejneru. V tomto článku publikujeme aplikaci ASP.NET Core do ACR.

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* [Vývojové nástroje .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) pro vývoj pomocí .NET Core
* Pokud chcete publikovat Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Instalace a nastavení

Pro instalaci Docker si nejdřív přečtěte informace v části [Docker Desktop for Windows: co je potřeba před instalací](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)nástroje. Dále nainstalujte [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Přidání projektu do kontejneru Docker

1. Vytvořte nový projekt pomocí šablony **ASP.NET Core webové aplikace** , nebo pokud chcete použít .NET Framework místo .NET Core, vyberte **ASP.NET webová aplikace (.NET Framework)**.
1. Na obrazovce **Další informace** se ujistěte, že je zaškrtnuté políčko **Povolit podporu Docker** .

   ![Zaškrtávací políčko Povolit podporu Docker](../../media/container-tools/vs-2019/webapp-additional-information-31-docker.png)

   Snímek obrazovky ukazuje .NET Core; Pokud používáte .NET Framework, vypadá to trochu odlišně.

1. Vyberte požadovaný typ kontejneru (Windows nebo Linux) a klikněte na **vytvořit**.

## <a name="dockerfile-overview"></a>Souboru Dockerfile – přehled

*Souboru Dockerfile* je v projektu vytvořen recept pro vytvoření finální image Docker. Porozumění příkazům, které jsou v něm, najdete v [referenčních informacích k souboru Dockerfile](https://docs.docker.com/engine/reference/builder/) :

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication1/WebApplication1.csproj", "WebApplication1/"]
RUN dotnet restore "WebApplication1/WebApplication1.csproj"
COPY . .
WORKDIR "/src/WebApplication1"
RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
```

Předchozí *souboru Dockerfile* vychází z image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru. Pokud používáte .NET Framework, bude základní image odlišná.

Když je zaškrtnuté políčko **Konfigurovat pro protokol HTTPS** v dialogovém okně Nový projekt, *souboru Dockerfile* zpřístupňuje dva porty. Pro přenosy HTTP se používá jeden port; druhý port se používá pro protokol HTTPS. Pokud políčko není zaškrtnuté, bude pro přenosy HTTP vystaven jeden port (80).

## <a name="debug"></a>Ladění

V rozevíracím seznamu ladění na panelu nástrojů vyberte **Docker** a spusťte ladění aplikace. Může se zobrazit zpráva s výzvou k důvěřování certifikátu. Chcete-li pokračovat, vyberte možnost důvěryhodného certifikátu.

V okně **výstup** se zobrazí možnost **nástroje kontejneru** , kde se zobrazují akce, které probíhají. Poprvé může chvíli trvat, než se stáhne základní image, ale v dalších spuštěních je mnohem rychlejší.

>[!NOTE]
> Pokud potřebujete změnit porty pro ladění, můžete to udělat v *launchSettings.js* souboru. Viz [nastavení spuštění kontejneru](../../container-launch-settings.md).

## <a name="containers-window"></a>Okno kontejnery

Pokud máte Visual Studio 2019 verze 16,4 nebo novější, můžete použít okno **kontejnery** k zobrazení spuštěných kontejnerů na počítači a také imagí, které máte k dispozici.

Otevřete okno **kontejnery** pomocí vyhledávacího pole v integrovaném vývojovém prostředí (pokud ho chcete použít, stiskněte klávesu **CTRL** + **Q** ), zadejte `container` a zvolte okno **kontejnery** ze seznamu.

Okno **kontejnery** můžete připojit na vhodné místo, například pod editorem, přesunutím kolem a podle vodítek umístění okna.

V okně Najděte svůj kontejner a krok na každé kartě, abyste zobrazili proměnné prostředí, mapování portů, protokoly a systém souborů.

![Snímek okna kontejnerů](../../media/overview/vs-2019/container-tools-window.png)

Další informace najdete v tématu [zobrazení a diagnostika kontejnerů a imagí v aplikaci Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publikování imagí Docker

Jakmile se cyklus vývoje a ladění aplikace dokončí, můžete vytvořit provozní image aplikace.

1. Změňte rozevírací seznam konfigurace na **vydaná** a sestavte aplikaci.
1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **publikovat**.
1. V dialogovém okně **publikovat** vyberte kartu **Docker Container Registry** .

   ![Snímek obrazovky s dialogem publikovat – vyberte Docker Container Registry](../../media/container-tools/vs-2019/docker-container-registry.png)

1. Vyberte **vytvořit novou Azure Container Registry**.

   ![Snímek obrazovky dialogového okna pro publikování – vyberte vytvořit novou Azure Container Registry](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. Do pole **vytvořit nový Azure Container Registry** zadejte požadované hodnoty.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio][0]

1. Klikněte na **Vytvořit**. Dialog **publikovat** teď zobrazuje vytvořený registr.

   ![Snímek obrazovky s dialogem pro publikování zobrazující Azure Container Registry vytvořené](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Pokud chcete dokončit proces publikování image kontejneru do nově vytvořeného registru v Azure, klikněte na **Dokončit** .

   ![Snímek obrazovky znázorňující úspěšné publikování](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Další kroky

Kontejner teď můžete načíst z registru do libovolného hostitele, který podporuje spouštění imagí Docker, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
