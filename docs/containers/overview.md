---
title: Nástroje kontejneru sady Visual Studio ve Windows
description: Seznamte se s nástroji dostupnými ve Visual Studiu pro práci s Dockerem
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916568"
---
# <a name="container-tools-in-visual-studio"></a>Nástroje kontejneru v sadě Visual Studio

Nástroje obsažené v sadě Visual Studio pro vývoj s kontejnery jsou snadno použitelné a výrazně zjednodušit vytváření, ladění a nasazení pro kontejnerizované aplikace. Můžete pracovat s kontejnerem pro jeden projekt nebo použít orchestraci kontejneru s Docker Compose, Service Fabric nebo Kubernetes pro práci s více službami v kontejnerech.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Požadavky

* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core pro vývoj napříč platformami**
* Chcete-li publikovat do registru kontejnerů Azure, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Podpora Dockeru ve Visual Studiu

Podpora Dockeru je k dispozici pro projekty ASP.NET, ASP.NET core projekty a projekty konzoly .NET Core a .NET Framework.

Podpora pro Docker v sadě Visual Studio se v průběhu několika verzí změnila v reakci na potřeby zákazníků. Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu, a podporované možnosti se liší podle typu projektu a verze sady Visual Studio. U některých podporovaných typů projektů, pokud chcete kontejner pouze pro jeden projekt, bez použití orchestrace, můžete to udělat přidáním podpory Dockeru.  Další úroveň je podpora orchestrace kontejneru, která přidá vhodné soubory podpory pro konkrétní orchestrátor, který zvolíte.  

S Visual Studio 2017 můžete použít Docker Compose a Service Fabric jako služby orchestrace kontejnerů.  Kubernetes můžete použít také v případě, že nainstalujete [nástroje Visual Studio pro Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).

> [!NOTE]
> Pokud používáte verzi Visual Studia 2017 před 15.8 nebo používáte šablonu projektu rozhraní .NET Framework (ne .NET Core), když přidáte podporu Dockeru, podpora orchestrace pomocí Docker Compose se přidá automaticky. Podpora orchestrace kontejnerů, přes Docker Compose, se přidá automaticky ve verzích Visual Studia 2017 15.0 až 15.7 a pro projekty rozhraní .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Požadavky

* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core**
* [Nástroje .NET Core Development Tools](https://dotnet.microsoft.com/download/dotnet-core/) pro vývoj s rozhraním .NET Core.
* Chcete-li publikovat do registru kontejnerů Azure, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Podpora Dockeru ve Visual Studiu

Podpora Dockeru je k dispozici pro projekty ASP.NET, ASP.NET core projekty a projekty konzoly .NET Core a .NET Framework.

Podpora pro Docker v sadě Visual Studio se v průběhu několika verzí změnila v reakci na potřeby zákazníků. Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu, a podporované možnosti se liší podle typu projektu a verze sady Visual Studio. U některých podporovaných typů projektů, pokud chcete kontejner pouze pro jeden projekt, bez použití orchestrace, můžete to udělat přidáním podpory Dockeru.  Další úroveň je podpora orchestrace kontejneru, která přidá vhodné soubory podpory pro konkrétní orchestrátor, který zvolíte.  

S Visual Studio 2019 můžete použít Docker Compose, Kubernetes a Service Fabric jako služby orchestrace kontejnerů.

> [!NOTE]
> Pokud používáte úplnou šablonu projektu konzoly rozhraní .NET Framework, je podporovanou možností **přidat podporu orchestratoru kontejneru** po vytvoření projektu s možnostmi použití service fabric nebo Docker Compose. Přidání podpory při vytváření projektu a **přidání podpory Dockeru** pro jeden projekt bez orchestrace nejsou k dispozici možnosti.

V sadě Visual Studio 2019 verze 16.4 a novější je k dispozici okno **Kontejnery,** které umožňuje zobrazit spuštěné kontejnery, procházet dostupné obrázky, prohlížet proměnné prostředí, protokoly a mapování portů, zkontrolovat souborový systém, připojit ladicí program nebo otevřít okno terminálu uvnitř prostředí kontejneru. Viz [Zobrazení a diagnostika kontejnerů a obrázků v sadě Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Přidání podpory Dockeru

Podporu Dockeru můžete povolit během vytváření projektu tak, že při vytváření nového projektu vyberete **Povolit podporu Dockeru,** jak je znázorněno na následujícím snímku obrazovky:

::: moniker range="vs-2017"
![Povolení podpory Dockeru pro novou ASP.NET základní webovou aplikaci ve Visual Studiu](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Povolení podpory Dockeru pro novou ASP.NET základní webovou aplikaci ve Visual Studiu](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Pro projekty rozhraní .NET Framework (nikoli .NET Core) jsou k dispozici pouze kontejnery systému Windows.

Podporu Dockeru můžete přidat do existujícího projektu výběrem **možnosti Přidat** > **podporu Dockeru** v **Průzkumníku řešení**. Příkazy **Přidat podporu dockeru >** dockeru a přidat > **orchestrator kontejneru jsou** umístěny v nabídce pravým tlačítkem myši (nebo kontextové nabídce) uzlu projektu pro projekt ASP.NET Core v **Průzkumníku řešení**, jak je znázorněno na následujícím snímku obrazovky:

![Přidat možnost nabídky podpory Dockeru v sadě Visual Studio](./media/overview/add-docker-support-menu.png)

Když přidáte nebo povolíte podporu Dockeru, Visual Studio přidá do projektu následující:

- soubor *Dockerfile*
- soubor .dockerignore
- Odkaz na balíček NuGet na cíle Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
Řešení vypadá takto, jakmile přidáte podporu Dockeru:

![Snímek obrazovky průzkumníka řešení se souborem Dockerfile a .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Když povolíte podporu Dockeru během vytváření projektu pro ASP.NET projektu (rozhraní .NET Framework, nikoli projekt .NET Core), jak je znázorněno na následujícím snímku obrazovky, je přidána také podpora orchestrace kontejneru.

![Povolení podpory dockeru pro ASP.NET projekt](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Podpora pro Docker Compose

Pokud chcete vytvořit řešení s více kontejnery pomocí Docker Compose, přidejte podporu orchestrace kontejnerů do vašich projektů. To umožňuje spustit a ladit skupinu kontejnerů (celé řešení nebo skupinu projektů) současně, pokud jsou definovány ve stejném souboru *docker-compose.yml.*

Chcete-li přidat podporu orchestrace kontejnerů pomocí funkce Docker Compose, klepněte pravým tlačítkem myši na uzel řešení nebo uzel projektu v **Průzkumníku řešení**a zvolte **Přidat podporu orchestrace kontejneru >**. Pak zvolte **Docker Compose** pro správu kontejnerů.

Po přidání podpory orchestrace kontejneru do projektu se zobrazí *dockerfile* přidaný do projektu (pokud tam ještě nebyl) a složka **docker-compose** přidaná do řešení v **Průzkumníku řešení**, jak je znázorněno zde:

![Soubory Dockeru v Průzkumníkovi řešení v Sadě Visual Studio](media/overview/docker-support-solution-explorer.png)

Pokud *docker-compose.yml* již existuje, Visual Studio pouze přidá požadované řádky konfiguračního kódu.

Opakujte proces s ostatními projekty, které chcete řídit pomocí Docker Compose.

## <a name="kubernetes-support"></a>Podpora pro Kubernetes

::: moniker range="vs-2017"
Chcete-li přidat podporu Kubernetes, nainstalujte [nástroje Visual Studio pro Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

S podporou Kubernetes můžete povolit připojení mezi místním projektem a clusterem Kubernetes spuštěným ve [službě Azure Kubernetes Service (AKS)](/azure/aks)a tím upravit a ladit služby spuštěné v AKS pomocí sady Visual Studio.  Tuto službu poskytuje [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). Azure Dev Spaces také umožňuje nastavit samostatné větve služeb Kubernetes s názvem *vývojové prostory* pro účely vývoje, takže můžete efektivně izolovat produkční služby od pracovních verzí ve vývoji a udržovat odlišné změny čistě oddělené od sebe navzájem.

Chcete-li přidat podporu Kubernetes do vašich projektů, zvolte **Kubernetes/Helm** při přidání podpory orchestrace kontejnerů. Do projektu se přidá několik souborů, včetně *azds.yaml*, který konfiguruje Azure Dev Spaces, a grafy helmu, které popisují strukturu vašich služeb Kubernetes.

## <a name="service-fabric-support"></a>Podpora pro Service Fabric

Pomocí nástrojů Service Fabric v Sadě Visual Studio můžete vyvíjet a ladit azure service fabric, spouštět a ladit místně a nasadit do Azure.

::: moniker range="vs-2017"
Visual Studio 2017 verze 15.9 a novější s nainstalovanou úlohou pro vývoj Azure podporuje vývoj kontejnerizovaných mikroslužeb pomocí kontejnerů Windows a orchestrace Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 podporuje vývoj kontejnerizovaných mikroslužeb pomocí kontejnerových kontejnerů systému Windows a orchestraci service fabric.
::: moniker-end

Podrobný kurz najdete v [tématu: Nasazení aplikace .NET v kontejneru Windows do Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Další informace o Azure Service Fabric, najdete v [tématu Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Průběžné doručování a průběžná integrace (CI/CD)

Visual Studio se snadno integruje s Azure Pipelines pro automatizovanou a průběžnou integraci a doručování změn do kódu služby a konfigurace. Pokud chcete začít, [přečtěte si informace o vytvoření prvního kanálu](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Pro Service Fabric, [najdete v tématu: Nasazení aplikace ASP.NET Core na Azure Service Fabric pomocí Azure DevOps projects](/azure/devops-project/azure-devops-project-service-fabric).

Kubernetes najdete [v tématu Nasazení aplikace kontejneru Dockeru do služby Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Další kroky

Další podrobnosti o implementaci služeb a použití nástrojů sady Visual Studio pro práci s kontejnery naleznete v následujících článcích:

[Ladění aplikací v místním kontejneru Dockeru](edit-and-refresh.md)

[Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio](hosting-web-apps-in-docker.md)
