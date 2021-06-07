---
title: Visual Studio Container Tools s ASP.NET Core
author: ghogen
description: Naučte se používat nástroje Visual Studio 2017 a Docker for Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 53bf0d559d9737494567b079621879b97a403a95
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2021
ms.locfileid: "111564695"
---
S Visual Studio můžete snadno sestavovat, ladit a spouštět kontejnerizované aplikace ASP.NET Core a publikovat je do služby Azure Container Registry (ACR), Docker Hub, Azure App Service nebo vlastního registru kontejnerů. V tomto článku budeme publikovat do ACR.

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **Vývoj** webu, **Nástroje Azure** a/nebo Vývoj pro **různé platformy v .NET Core**
* Publikování do Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Dockeru si nejprve projděte informace v [docker Desktopu pro Windows: Co](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)potřebujete vědět před instalací . Dále nainstalujte [Docker Desktop.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="add-a-project-to-a-docker-container"></a>Přidání projektu do kontejneru Dockeru

1. V nabídce Visual Studio vyberte **File (Soubor) > New > Project (Nový projekt >).**
1. V části **Šablony** dialogového **okna Nový** projekt vyberte **Visual C# > Web.**
1. Vyberte **ASP.NET Core Web Application** nebo pokud chcete použít .NET Framework místo .NET Core, vyberte ASP.NET Webová **aplikace.**
1. Zadejte název nové aplikace (nebo vezměte výchozí nastavení) a vyberte **OK.**
1. Vyberte **Web Application (Webová aplikace).**
1. Zaškrtněte políčko **Povolit podporu Dockeru.**

   ![Povolení podpory Dockeru – zaškrtávací políčko](../../media/container-tools/enable-docker-support.PNG)

   Snímek obrazovky ukazuje .NET Core. Pokud používáte jiný .NET Framework, vypadá trochu jinak.

1. Vyberte typ kontejneru, který chcete (Windows nebo Linux) a klikněte na **OK.**

## <a name="dockerfile-overview"></a>Přehled souboru Dockerfile

V projektu se vytvoří soubor *Dockerfile*, recept na vytvoření konečné image Dockeru. Informace o příkazech v souboru [Dockerfile](https://docs.docker.com/engine/reference/builder/) najdete v referenčních informacích:

```
FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Předchozí soubor *Dockerfile* vychází z image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru. Pokud používáte základní image .NET Framework, základní image se bude lišit.

Když je zaškrtnuté políčko Konfigurovat pro **HTTPS** v dialogovém okně nového projektu, *soubor Dockerfile* zpřístupní dva porty. Jeden port se používá pro provoz HTTP. Druhý port se používá pro PROTOKOL HTTPS. Pokud políčko není zaškrtnuté, pro provoz HTTP se zobrazí jeden port (80).

## <a name="debug"></a>Ladění

V rozevíracím seznamu ladění na panelu nástrojů vyberte **Docker** a spusťte ladění aplikace. Může se zobrazit zpráva s výzvou o důvěřování certifikátu. Zvolte, že chcete certifikátu důvěřovat, aby pokračoval.

V **okně** Výstup se zobrazí akce, které prochádí.

Otevřete **konzolu Správce balíčků** (PMC) z nabídky **Nástroje**> NuGet Správce balíčků a **Správce balíčků konzoly.**

Výsledná image Dockeru aplikace je označená jako *dev*. Image je založená na *značce 2.1-aspnetcore-runtime* základní image *microsoft/dotnet.* V `docker images` okně konzoly **Správce balíčků** (PMC) spusťte příkaz . Zobrazí se obrázky na počítači:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Vývojová** image neobsahuje binární soubory aplikace a další  obsah, protože konfigurace ladění používají připojení svazku k zajištění iterativního prostředí pro úpravy a ladění. Pokud chcete vytvořit produkční image obsahující veškerý obsah, použijte **konfiguraci Vydání.**

Spusťte příkaz `docker ps` v PMC. Všimněte si, že aplikace je spuštěná pomocí kontejneru:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Publikování imagí Dockeru

Po dokončení cyklu vývoje a ladění aplikace můžete vytvořit produkční image aplikace.

1. Změňte rozevírací seznam konfigurace na **Release (Verze)** a sestavte aplikaci.
1. Klikněte pravým tlačítkem na projekt **v Průzkumník řešení** a zvolte **Publikovat.**
1. V dialogovém okně cíl publikování vyberte kartu **Container Registry** publikování.
1. Zvolte **Vytvořit nový Azure Container Registry** a klikněte na **Publikovat.**
1. Do pole Create a new (Vytvořit nový) **zadejte požadované Azure Container Registry**.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které chcete vytvořit registr kontejneru. Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění blízko vás | Zvolte Umístění v oblasti [blízko](https://azure.microsoft.com/regions/) vás nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Visual Studio dialogového okna Azure Container Registry vytvoření][0]

1. Klikněte na **Vytvořit**.

## <a name="next-steps"></a>Další kroky

Kontejner teď můžete stáhnout z registru na libovolného hostitele, který dokáže spustit image Dockeru, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
