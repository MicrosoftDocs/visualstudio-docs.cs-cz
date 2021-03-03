---
title: Nástroje kontejneru sady Visual Studio s ASP.NET Core a React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Naučte se vytvářet aplikace s podporou zabezpečeného ověřování pomocí kontejnerů v nástroji Visual Studio Container Tools a Docker
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 7a2a9e7c8b2c53dcee7f11d4b0b795b66ab80a80
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684355"
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
* [Vývojové nástroje .NET core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) pro vývoj pomocí .net Core 3,1.
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

   ![Snímek obrazovky s novým projektem React.js](media/container-tools-react/vs-2017/new-react-project.png)

1. Klikněte pravým tlačítkem na uzel projektu a vyberte **Přidat** > **podporu Docker** a přidejte do svého projektu souboru Dockerfile.

   ![Přidání podpory Dockeru](media/container-tools-react/vs-2017/add-docker-support.png)

1. Vyberte typ kontejneru a klikněte na tlačítko **OK**.
::: moniker-end

::: moniker range=">=vs-2019"

1. Vytvořte nový projekt pomocí **ASP.NET Core se** šablonou React.js.

   ![Snímek obrazovky s vytvořením nového projektu React.js](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. Na obrazovce **Další informace** nemůžete vybrat možnost **Povolit podporu Docker**, ale nedělejte si starosti, můžete tuto podporu přidat později.

   ![Snímek obrazovky s vytvořením nového projektu React.js – obrazovka Další informace](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Klikněte pravým tlačítkem na uzel projektu a vyberte **Přidat** > **podporu Docker** a přidejte do svého projektu souboru Dockerfile.

   ![Přidání podpory Dockeru](media/container-tools-react/vs-2017/add-docker-support.png)

1. Vyberte typ kontejneru.
::: moniker-end

Další krok se liší v závislosti na tom, jestli používáte kontejnery Linux nebo kontejnery Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Úprava souboru Dockerfile (kontejnery Linux)

*Souboru Dockerfile* je v projektu vytvořen recept pro vytvoření finální image Docker. Porozumění příkazům, které jsou v něm, najdete v [referenčních informacích k souboru Dockerfile](https://docs.docker.com/engine/reference/builder/) .

Otevřete *souboru Dockerfile* v projektu a přidejte následující řádky pro instalaci Node.js 10. x do kontejneru. Nezapomeňte přidat tyto řádky v první části, chcete-li přidat instalaci správce balíčků node *npm.exe* do základní image a také v `build` části.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Souboru Dockerfile* by teď měl vypadat nějak takto:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication-ReactSPA/WebApplication-ReactSPA.csproj", "WebApplication-ReactSPA/"]
RUN dotnet restore "WebApplication-ReactSPA/WebApplication-ReactSPA.csproj"
COPY . .
WORKDIR "/src/WebApplication-ReactSPA"
RUN dotnet build "WebApplication-ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-ReactSPA.dll"]
```

Předchozí *souboru Dockerfile* je založen na imagi [MCR.Microsoft.com/dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru.

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

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

   1. Aktualizujte soubor. dockerignore odebráním `**/bin` .

## <a name="debug"></a>Ladění

V rozevíracím seznamu ladění na panelu nástrojů vyberte **Docker** a spusťte ladění aplikace. Může se zobrazit zpráva s výzvou k důvěřování certifikátu. Chcete-li pokračovat, vyberte možnost důvěryhodného certifikátu.  Při prvním sestavení, Docker stáhne základní image, takže může trvat delší dobu.

V okně **výstup** se zobrazí možnost **nástroje kontejneru** , kde se zobrazují akce, které probíhají. Měli byste vidět kroky instalace přidružené k *npm.exe*.

V prohlížeči se zobrazí domovská stránka aplikace.

::: moniker range="vs-2017"
   ![Snímek obrazovky běžící aplikace](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Snímek obrazovky běžící aplikace](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Zkuste přejít na stránku *čítače* a otestovat kód na straně klienta pro čítač kliknutím na tlačítko **přírůstek** .

Otevřete **konzolu Správce balíčků** (PMC) z **nástrojů** nabídky> správce balíčků NuGet, **Konzola správce balíčků**.

Výsledná image Docker aplikace je označená jako *vývoj*. Obrázek je založen na značce *3,1-nanoserver-1903* základní image *dotnet/Core/ASPNET* . Spusťte `docker images` příkaz v okně **konzoly Správce balíčků** (PMC). Zobrazí se obrázky na počítači:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1-buster-slim     e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> **Vývojová** image neobsahuje binární soubory aplikace a další obsah, protože konfigurace **ladění** používá k zajištění iterativního prostředí pro iterativní úpravu a ladění připojení svazků. Pokud chcete vytvořit produkční image obsahující veškerý obsah, použijte konfiguraci **vydané verze** .

Spusťte `docker ps` příkaz v PMC. Všimněte si, že aplikace je spuštěná pomocí kontejneru:

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>Publikování imagí Docker

Jakmile se cyklus vývoje a ladění aplikace dokončí, můžete vytvořit provozní image aplikace.

:::moniker range="vs-2017"

1. Změňte rozevírací seznam konfigurace na **vydaná** a sestavte aplikaci.
1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **publikovat**.
1. V dialogovém okně Publikovat cíl vyberte možnost **Container Registry**.
1. Vyberte **vytvořit novou Azure Container Registry** a klikněte na **publikovat**.
1. Do pole **vytvořit nový Azure Container Registry** zadejte požadované hodnoty.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. Vyberte **Vytvořit**.

   ![Snímek obrazovky znázorňující úspěšné publikování](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Změňte rozevírací seznam konfigurace na **vydaná** a sestavte aplikaci.
1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **publikovat**.
1. V dialogovém okně Publikovat cíl vyberte **docker Container Registry**.

   ![Zvolit Docker Container Registry](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Pak vyberte **Azure Container Registry**.

   ![Zvolit Azure Container Registry](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. Vyberte možnost **vytvořit nový Azure Container Registry**.
1. Na obrazovce **vytvořit novou Azure Container Registry** zadejte požadované hodnoty.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které se má vytvořit registr kontejneru Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění, které je blízko vás | Vyberte umístění v [oblasti](https://azure.microsoft.com/regions/) poblíž nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Dialog pro vytváření Azure Container Registry v aplikaci Visual Studio](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. Vyberte **vytvořit** a pak vyberte **Dokončit**.

   ![Vybrat nebo vytvořit nové ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   Po skončení procesu publikování můžete zkontrolovat nastavení publikování a v případě potřeby je upravit nebo znovu publikovat obrázek pomocí tlačítka **publikovat** .

   ![Snímek obrazovky znázorňující úspěšné publikování](media/container-tools-react/vs-2019/publish-finished.png)

   Chcete-li se znovu spustit pomocí dialogového okna **publikovat** , odstraňte profil publikování pomocí odkazu **Odstranit** na této stránce a pak znovu klikněte na tlačítko **publikovat** .
:::moniker-end

## <a name="next-steps"></a>Další kroky

Kontejner teď můžete načíst z registru do libovolného hostitele, který podporuje spouštění imagí Docker, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Další zdroje informací

* [Vývoj kontejnerů pomocí sady Visual Studio](./index.yml)
* [Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru](troubleshooting-docker-errors.md)
* [Úložiště GitHub pro Visual Studio Container Tools](https://github.com/Microsoft/DockerTools)

