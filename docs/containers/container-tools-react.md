---
title: Nástroje kontejneru sady Visual Studio s ASP.NET Core a React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Naučte se používat nástroje sady Visual Studio Container a Docker for Windows
ms.author: ghogen
ms.date: 05/14/2020
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 45dc1f16f1655c5c738804a1c4e0093dd9c8b1f8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036324"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Rychlý Start: použití Docker s nareagující jednostránkové aplikace v aplikaci Visual Studio

Pomocí sady Visual Studio můžete snadno sestavovat, ladit a spouštět ASP.NET Core aplikace s kontejnerem, včetně těch, které jsou s JavaScriptem na straně klienta, jako je například React.js jednostránkové aplikace, a publikovat je do Azure Container Registry (ACR), Docker Hub, Azure App Service nebo vlastního registru kontejneru. V tomto článku budeme publikovat na ACR.

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* Pokud chcete publikovat Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Pro kontejnery Windows, Windows 10 verze 1903 nebo novější, pro používání imagí Docker, na které se odkazuje v tomto článku.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* [Vývojové nástroje .NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pro vývoj pomocí .net Core 2,2
* Pokud chcete publikovat Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Pro kontejnery Windows, Windows 10 verze 1903 nebo novější, pro používání imagí Docker, na které se odkazuje v tomto článku.
::: moniker-end

## <a name="installation-and-setup"></a>Instalace a nastavení

Pro instalaci Docker si nejdřív přečtěte informace v části [Docker Desktop for Windows: co je potřeba před instalací](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)nástroje. Dále nainstalujte [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Vytvořit projekt a přidat podporu Docker

::: moniker range="vs-2017"
1. Vytvořte nový projekt pomocí šablony **ASP.NET Core webové aplikace** .
1. Vyberte **React.js**. Nemůžete vybrat možnost **Povolit podporu Docker**, ale nedělejte si starosti, můžete tuto podporu přidat po vytvoření projektu.

   ![Snímek obrazovky s novým projektem React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Klikněte pravým tlačítkem na uzel projektu a vyberte **Přidat** > **podporu Docker** a přidejte do svého projektu souboru Dockerfile.

   ![Přidání podpory Dockeru](media/container-tools-react/vs2017/add-docker-support.png)

1. Vyberte typ kontejneru a klikněte na tlačítko **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Vytvořte nový projekt pomocí šablony **ASP.NET Core webové aplikace** .
1. Vyberte **React.js**a klikněte na **vytvořit**. Nemůžete vybrat možnost **Povolit podporu Docker**, ale nedělejte si starosti, můžete tuto podporu přidat později.

   ![Snímek obrazovky s novým projektem React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Klikněte pravým tlačítkem na uzel projektu a vyberte **Přidat** > **podporu Docker** a přidejte do svého projektu souboru Dockerfile.

   ![Přidání podpory Dockeru](media/container-tools-react/vs2017/add-docker-support.png)

1. Vyberte typ kontejneru.
::: moniker-end

Další krok se liší v závislosti na tom, jestli používáte kontejnery Linux nebo kontejnery Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Úprava souboru Dockerfile (kontejnery Linux)

*Souboru Dockerfile*je v projektu vytvořen recept pro vytvoření finální image Docker. Porozumění příkazům, které jsou v něm, najdete v [referenčních informacích k souboru Dockerfile](https://docs.docker.com/engine/reference/builder/) .

Otevřete *souboru Dockerfile* v projektu a přidejte následující řádky pro instalaci Node.js 10. x do kontejneru. Nezapomeňte přidat tyto řádky v první části, chcete-li přidat instalaci správce balíčků node *npm.exe* do základní image a také v `build` části.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Souboru Dockerfile* by teď měl vypadat nějak takto:

```Dockerfile
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

Předchozí *souboru Dockerfile* vychází z image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru.

Když je zaškrtnuté políčko **Konfigurovat pro protokol HTTPS** v dialogovém okně Nový projekt, *souboru Dockerfile* zpřístupňuje dva porty. Pro přenosy HTTP se používá jeden port; druhý port se používá pro protokol HTTPS. Pokud políčko není zaškrtnuté, bude pro přenosy HTTP vystaven jeden port (80).

## <a name="modify-the-dockerfile-windows-containers"></a>Úprava souboru Dockerfile (kontejnery Windows)

Otevřete soubor projektu dvojitým kliknutím na uzel projektu a aktualizujte soubor projektu (*. csproj) tak, že přidáte následující vlastnost jako podřízený `<PropertyGroup>` prvek elementu:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aktualizujte souboru Dockerfile přidáním následujících řádků. Tato akce zkopíruje uzel a npm do kontejneru.

   1. Přidat ``# escape=` `` na první řádek souboru Dockerfile
   1. Přidejte následující řádky před `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Přidejte následující řádek před a za `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Úplný souboru Dockerfile by teď měl vypadat nějak takto:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

   1. Aktualizujte soubor. dockerignore odebráním `**/bin` .

## <a name="debug"></a>Ladění

V rozevíracím seznamu ladění na panelu nástrojů vyberte **Docker** a spusťte ladění aplikace. Může se zobrazit zpráva s výzvou k důvěřování certifikátu. Chcete-li pokračovat, vyberte možnost důvěryhodného certifikátu.  Při prvním sestavení, Docker stáhne základní image, takže může trvat delší dobu.

V okně **výstup** se zobrazí možnost **nástroje kontejneru** , kde se zobrazují akce, které probíhají. Měli byste vidět kroky instalace přidružené k *npm.exe*.

V prohlížeči se zobrazí domovská stránka aplikace.

::: moniker range="vs-2017"
   ![Snímek obrazovky běžící aplikace](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Snímek obrazovky běžící aplikace](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Zkuste přejít na stránku *čítače* a otestovat kód na straně klienta pro čítač kliknutím na tlačítko **přírůstek** .

Otevřete **konzolu Správce balíčků** (PMC) z **nástrojů** nabídky> správce balíčků NuGet, **Konzola správce balíčků**.

Výsledná image Docker aplikace je označená jako *vývoj*. Obrázek je založen na značce *2,2-aspnetcore-runtime* základní image *Microsoft/dotNET* . Spusťte `docker images` příkaz v okně **konzoly Správce balíčků** (PMC). Zobrazí se obrázky na počítači:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Vývojová** image neobsahuje binární soubory aplikace a další obsah, protože konfigurace **ladění** používá k zajištění iterativního prostředí pro iterativní úpravu a ladění připojení svazků. Pokud chcete vytvořit produkční image obsahující veškerý obsah, použijte konfiguraci **vydané verze** .

Spusťte `docker ps` příkaz v PMC. Všimněte si, že aplikace je spuštěná pomocí kontejneru:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

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
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[Skladová jednotka (SKU)](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio][0]

1. Klikněte na **Vytvořit**.

   ![Snímek obrazovky znázorňující úspěšné publikování](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Další kroky

Kontejner teď můžete načíst z registru do libovolného hostitele, který podporuje spouštění imagí Docker, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Další zdroje

* [Vývoj kontejnerů pomocí sady Visual Studio](./index.yml)
* [Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru](troubleshooting-docker-errors.md)
* [Úložiště GitHub pro Visual Studio Container Tools](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end