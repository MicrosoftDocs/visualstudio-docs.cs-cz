---
title: Nástroje kontejneru sady Visual Studio ve Windows
description: Získejte informace o nástrojích, které jsou k dispozici v aplikaci Visual Studio pro práci s Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916568"
---
# <a name="container-tools-in-visual-studio"></a>Nástroje kontejneru v sadě Visual Studio

Nástroje zahrnuté v aplikaci Visual Studio pro vývoj s kontejnery se snadno používají a významně zjednodušují sestavování, ladění a nasazování pro kontejnery aplikací. Můžete pracovat s kontejnerem pro jeden projekt nebo orchestrace kontejnerů pomocí Docker Compose, Service Fabric nebo Kubernetes pro práci s více službami v kontejnerech.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* Pokud chcete publikovat Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Podpora Docker v aplikaci Visual Studio

Podpora Docker je k dispozici pro projekty ASP.NET, projekty ASP.NET Core a projekty konzoly .NET Core a .NET Framework.

Podpora Docker v aplikaci Visual Studio se v reakci na potřeby zákazníka změnila v několika verzích. Existují dvě úrovně podpory Docker, které můžete přidat do projektu a podporované možnosti se liší podle typu projektu a verze aplikace Visual Studio. U některých podporovaných typů projektů, pokud chcete pouze kontejner pro jeden projekt bez použití orchestrace, můžete to provést přidáním podpory Docker.  Další úrovní je podpora orchestrace kontejnerů, která umožňuje přidat vhodné podpůrné soubory pro konkrétní produkt Orchestrator, který zvolíte.  

V rámci sady Visual Studio 2017 můžete použít Docker Compose a Service Fabric jako služby pro orchestraci kontejnerů.  Kubernetes můžete použít také v případě, že nainstalujete [Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).

> [!NOTE]
> Pokud používáte verzi sady Visual Studio 2017 před 15,8 nebo pokud používáte šablonu projektu .NET Framework (ne .NET Core), při přidání podpory Docker se podpora orchestrace pomocí Docker Compose přidá automaticky. Podpora orchestrace kontejnerů prostřednictvím Docker Compose je automaticky přidána do sady Visual Studio 2017 verze 15,0 do 15,7 a pro .NET Framework projekty.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* [Vývojové nástroje .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) pro vývoj pomocí .NET Core.
* Pokud chcete publikovat Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Podpora Docker v aplikaci Visual Studio

Podpora Docker je k dispozici pro projekty ASP.NET, projekty ASP.NET Core a projekty konzoly .NET Core a .NET Framework.

Podpora Docker v aplikaci Visual Studio se v reakci na potřeby zákazníka změnila v několika verzích. Existují dvě úrovně podpory Docker, které můžete přidat do projektu a podporované možnosti se liší podle typu projektu a verze aplikace Visual Studio. U některých podporovaných typů projektů, pokud chcete pouze kontejner pro jeden projekt bez použití orchestrace, můžete to provést přidáním podpory Docker.  Další úrovní je podpora orchestrace kontejnerů, která umožňuje přidat vhodné podpůrné soubory pro konkrétní produkt Orchestrator, který zvolíte.  

Pomocí sady Visual Studio 2019 můžete použít Docker Compose, Kubernetes a Service Fabric jako služby pro orchestraci kontejnerů.

> [!NOTE]
> Používáte-li úplnou .NET Framework šablonu projektu konzoly, je podporovaná možnost **Přidat kontejner Orchestrator support** po vytvoření projektu s možnostmi pro použití Service Fabric nebo Docker Compose. Přidání podpory při vytváření projektu a **Přidání podpory Docker** pro jeden projekt bez orchestrace nejsou k dispozici možnosti.

V aplikaci Visual Studio 2019 verze 16,4 a novější je k dispozici okno **kontejnery** , které umožňuje zobrazit spuštěné kontejnery, procházet dostupné obrázky, zobrazit proměnné prostředí, protokoly a mapování portů, zkontrolovat systém souborů, připojit ladicí program nebo otevřít okno terminálu v prostředí kontejneru. Viz [zobrazení a diagnostika kontejnerů a imagí v aplikaci Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Přidání podpory Docker

Podporu Docker můžete povolit během vytváření projektu výběrem možnosti **Povolit podporu Docker** při vytváření nového projektu, jak je znázorněno na následujícím snímku obrazovky:

::: moniker range="vs-2017"
![Povolit podporu Docker pro novou ASP.NET Core webovou aplikaci v aplikaci Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Povolit podporu Docker pro novou ASP.NET Core webovou aplikaci v aplikaci Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Pro .NET Framework projekty (ne .NET Core) jsou k dispozici pouze kontejnery Windows.

Podporu Docker můžete přidat do existujícího projektu výběrem možnosti **přidat** > **podporu docker** v **Průzkumník řešení**. Příkazy **přidat > podpora Docker** a **Přidat > kontejneru Orchestrator** jsou umístěné v místní nabídce (nebo v kontextové nabídce) uzlu projektu pro ASP.NET Core projektu v **Průzkumník řešení**, jak je znázorněno na následujícím snímku obrazovky:

![Přidat možnost nabídky Docker support v aplikaci Visual Studio](./media/overview/add-docker-support-menu.png)

Když přidáte nebo povolíte podporu Docker, Visual Studio přidá do projektu následující:

- soubor *souboru Dockerfile*
- soubor. dockerignore
- odkaz na balíček NuGet na Microsoft. VisualStudio. Azure. containers. Tools. targets

::: moniker range=">=vs-2019"
Toto řešení po přidání podpory Docker vypadá takto:

![Snímek obrazovky Průzkumníka řešení se souborem souboru Dockerfile a. dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Pokud povolíte podporu Docker během vytváření projektu pro projekt ASP.NET (.NET Framework, ne projekt .NET Core), jak je znázorněno na následujícím snímku obrazovky, je přidána i podpora orchestrace kontejnerů.

![Povolit podporu pro vytváření Docker pro projekt ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Podpora Docker Compose

Pokud chcete vytvořit řešení s více kontejnery pomocí Docker Compose, přidejte do svých projektů podporu orchestrace kontejnerů. To umožňuje spustit a ladit skupinu kontejnerů (celé řešení nebo skupiny projektů), pokud jsou definovány ve stejném souboru *Docker-Compose. yml* .

Chcete-li přidat podporu orchestrace kontejnerů pomocí Docker Compose, klikněte pravým tlačítkem myši na uzel řešení nebo projektu v **Průzkumník řešení**a vyberte možnost **Přidat > podporu orchestrace kontejnerů**. Pak zvolte **Docker Compose** pro správu kontejnerů.

Po přidání podpory orchestrace kontejnerů do projektu se zobrazí *souboru Dockerfile* do projektu (Pokud ještě neexistuje) a složka **Docker-Docker** , která je přidána do řešení v **Průzkumník řešení**, jak je znázorněno zde:

![Soubory Docker v Průzkumník řešení v aplikaci Visual Studio](media/overview/docker-support-solution-explorer.png)

Pokud *Docker-Compose. yml* už existuje, Visual Studio přidá do něj požadované řádky konfiguračního kódu.

Opakujte tento postup s ostatními projekty, které chcete řídit pomocí Docker Compose.

## <a name="kubernetes-support"></a>Podpora Kubernetes

::: moniker range="vs-2017"
Pokud chcete přidat podporu Kubernetes, nainstalujte [Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

Díky podpoře Kubernetes můžete povolit připojení mezi místním projektem a clusterem Kubernetes běžícím ve [službě Azure Kubernetes Service (AKS)](/azure/aks)a tím upravit a ladit vaše služby běžící v AKS pomocí sady Visual Studio.  Tuto službu poskytuje [Azure dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). Azure Dev Spaces taky umožňuje nastavit samostatné pobočky vašich služeb Kubernetes s názvem *vývojové prostory* pro účely vývoje, takže můžete efektivně izolovat produkční služby od pracovních verzí ve vývoji a udržovat jedinečné změny čistě oddělené od sebe navzájem.

Pokud chcete přidat podporu Kubernetes do projektů, vyberte **Kubernetes/Helm** , když přidáte podporu orchestrace kontejnerů. Do projektu se přidalo několik souborů, včetně *azds. yaml*, které konfiguruje Azure dev Spaces a Helm grafy, které popisují strukturu vašich služeb Kubernetes.

## <a name="service-fabric-support"></a>Podpora Service Fabric

Pomocí nástrojů Service Fabric v aplikaci Visual Studio můžete vyvíjet a ladit službu Azure Service Fabric, spouštět a ladit místně a nasazovat do Azure.

::: moniker range="vs-2017"
Visual Studio 2017 verze 15,9 a novější s nainstalovanou úlohou vývoj pro Azure podporuje vývoj kontejnerových mikroslužeb pomocí kontejnerů Windows a Service Fabric orchestrace.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 podporuje vývoj kontejnerových mikroslužeb pomocí kontejnerů Windows a Service Fabric orchestrace.
::: moniker-end

Podrobný kurz najdete v tématu [kurz: nasazení aplikace .NET v kontejneru Windows do Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Další informace o Azure Service Fabric najdete v článku [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Průběžné doručování a průběžná integrace (CI/CD)

Visual Studio se snadno integruje s Azure Pipelines pro automatizovanou a průběžnou integraci a doručování změn kódu a konfigurace služby. Informace o tom, jak začít, najdete v tématu [Vytvoření prvního kanálu](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Service Fabric najdete v tématu [kurz: nasazení ASP.NET Core aplikace do Azure Service Fabric pomocí Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Kubernetes najdete v tématu [nasazení aplikace kontejneru Docker do služby Azure Kubernetes](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Další kroky

Další podrobnosti o implementaci služeb a používání nástrojů sady Visual Studio pro práci s kontejnery najdete v následujících článcích:

[Ladění aplikací v místním kontejneru Docker](edit-and-refresh.md)

[Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio](hosting-web-apps-in-docker.md)
