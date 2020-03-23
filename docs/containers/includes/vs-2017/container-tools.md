---
title: Nástroje kontejnerů visual studia s jádrem ASP.NET
author: ghogen
description: Přečtěte si, jak používat nástroje Visual Studio 2017 a Docker pro Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ae6548892010035564bf29a8eda25b736db97d2a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922986"
---
Pomocí Visual Studia můžete snadno vytvářet, ladit a spouštět kontejnerizované aplikace ASP.NET Core a publikovat je do registru kontejnerů Azure (ACR), Docker Hubu, služby Azure App Service nebo vlastního registru kontejnerů. V tomto článku budeme publikovat do ACR.

## <a name="prerequisites"></a>Požadavky

* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core pro vývoj napříč platformami**
* Chcete-li publikovat do registru kontejnerů Azure, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Dockeru nejprve zkontrolujte informace na [ploše Dockeru pro Windows: Co je třeba vědět před instalací](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Dále nainstalujte [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Přidání projektu do kontejneru Dockeru

1. V nabídce Visual Studio vyberte **Soubor > Nový > Project**.
1. V části **Šablony** v dialogovém okně **Nový projekt** vyberte **položku Visual C# > Web**.
1. Vyberte **ASP.NET základní webovou aplikaci** nebo pokud chcete místo rozhraní .NET Core použít rozhraní .NET Core, vyberte **možnost ASP.NET webová aplikace**.
1. Pojmenujte novou aplikaci (nebo převezměte výchozí) a vyberte **OK**.
1. Vyberte **webovou aplikaci**.
1. Zaškrtněte políčko **Povolit podporu Dockeru.**

   ![Zaškrtávací políčko Povolit podporu Dockeru](../../media/container-tools/enable-docker-support.PNG)

   Snímek obrazovky zobrazuje jádro .NET; Pokud používáte rozhraní .NET Framework, vypadá to trochu jinak.

1. Vyberte požadovaný typ kontejneru (Windows nebo Linux) a klepněte na tlačítko **OK**.

## <a name="dockerfile-overview"></a>Přehled souborů Dockeru

*Dockerfile*, recept pro vytvoření konečné image Dockeru, je vytvořen v projektu. Naleznete [na Dockerfile odkaz](https://docs.docker.com/engine/reference/builder/) pro pochopení příkazů v něm.:

```
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM microsoft/dotnet:2.1-sdk AS build
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

Předchozí *soubor Dockerfile* je založen na image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní bitové kopie vytvořením projektu a jeho přidáním do kontejneru. Pokud používáte rozhraní .NET Framework, základní bitová kopie se bude lišit.

Když je zaškrtnuto políčko **Konfigurovat pro protokol HTTPS** nového dialogového okna projektu, *dockerfile* zpřístupní dva porty. Jeden port se používá pro přenosy HTTP; druhý port se používá pro protokol HTTPS. Pokud políčko není zaškrtnuto, jeden port (80) je vystaven pro přenosy HTTP.

## <a name="debug"></a>Ladění

Vyberte **Docker** z rozevíracího okna ladění na panelu nástrojů a začněte ladit aplikaci. Může se zobrazit zpráva s výzvou k důvěře certifikátu. zvolte důvěřovat certifikátu, aby mohl pokračovat.

Okno **Výstup** ukazuje, jaké akce probíhají.

Otevřete **konzolu Správce balíčků** (PMC) v nabídce **Nástroje**> Správce balíčků NuGet, **konzola správce balíčků**.

Výsledná image Dockeru aplikace je označena jako *dev*. Obrázek je založen na značce *2.1-aspnetcore-runtime* základní bitové kopie *microsoft/dotnet.* Spusťte `docker images` příkaz v okně **Konzola správce balíčků** (PMC). Obrázky na zařízení jsou zobrazeny:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Obrázek dev** neobsahuje binární soubory aplikace a další obsah, protože konfigurace **ladění** používají připojení svazku k zajištění iterativního prostředí pro úpravy a ladění. Chcete-li vytvořit produkční bitovou kopii obsahující veškerý obsah, použijte konfiguraci **vydání.**

Spusťte `docker ps` příkaz v PMC. Všimněte si, že aplikace běží pomocí kontejneru:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

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

## <a name="next-steps"></a>Další kroky

Nyní můžete vytáhnout kontejner z registru na libovolného hostitele schopného spouštět ibi Dockeru, například [instance kontejneru Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
