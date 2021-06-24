---
title: Visual Studio Container Tools s ASP.NET Core a React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Zjistěte, jak vytvořit kontejnerizovanou aplikaci React SPA s Visual Studio Container Tools a Dockerem.
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 177a44f8af73226d4352c4a48c23c65eadc3e608
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602030"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Rychlý start: Použití Dockeru s jedno stránkovou aplikací React v Visual Studio

S Visual Studio můžete snadno sestavovat, ladit React.js spouštět kontejnerizované aplikace ASP.NET Core, včetně aplikací s JavaScriptem na straně klienta, jako je jedno stránkovací aplikace, React.js publikovat je do služby Azure Container Registry (ACR), Docker Hub, Azure App Service nebo vlastního registru kontejnerů. V tomto článku budeme publikovat do ACR.

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **Vývoj** webu, **Nástroje Azure** a/nebo Vývoj pro **různé platformy v .NET Core**
* Publikování do Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Pro kontejnery Windows Windows 10 verze 1809 nebo novější k použití imagí Dockeru, na které odkazuje tento článek.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **Vývoj** webu, **Nástroje Azure** a/nebo Vývoj pro **různé platformy v .NET Core**
* [Vývojové nástroje .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) pro vývoj s .NET Core 3.1
* Publikování do Azure Container Registry, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Pro kontejnery Windows Windows 10 verze 1809 nebo novější k použití imagí Dockeru, na které odkazuje tento článek.
::: moniker-end

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Dockeru si nejprve projděte informace v [docker Desktopu pro Windows: Co](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)potřebujete vědět před instalací . Dále nainstalujte [Docker Desktop.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="create-a-project-and-add-docker-support"></a>Vytvoření projektu a přidání podpory Dockeru

::: moniker range="vs-2017"
1. Pomocí šablony webové aplikace **ASP.NET Core vytvořte nový** projekt.
1. Vyberte **React.js**. Nemůžete vybrat Povolit podporu **Dockeru,** ale nedělejte si starosti, tuto podporu můžete přidat po vytvoření projektu.

   ![Snímek obrazovky nového React.js projektu](media/container-tools-react/vs-2017/new-react-project.png)

1. Klikněte pravým tlačítkem na uzel projektu a zvolte **Přidat** > **podporu Dockeru** a přidejte do projektu soubor Dockerfile.

   ![Přidání podpory Dockeru](media/container-tools-react/vs-2017/add-docker-support.png)

1. Vyberte typ kontejneru a klikněte na **OK.**
::: moniker-end

::: moniker range=">=vs-2019"

1. Vytvořte nový projekt pomocí ASP.NET **Core s React.js** šablonou.

   ![Snímek obrazovky s vytvořením nového React.js projektu](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. Na **obrazovce Další** informace nemůžete vybrat Povolit podporu **Dockeru,** ale nedělejte si starosti, tuto podporu můžete přidat později.

   ![Snímek obrazovky s vytvořením React.js projektu – Další informace](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Klikněte pravým tlačítkem na uzel projektu a zvolte **Přidat** > **podporu Dockeru** a přidejte do projektu soubor Dockerfile.

   ![Přidání podpory Dockeru](media/container-tools-react/vs-2017/add-docker-support.png)

1. Vyberte typ kontejneru.
::: moniker-end

Další krok se liší v závislosti na tom, jestli používáte kontejnery Linuxu nebo kontejnery Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Úprava souboru Dockerfile (kontejnery Linuxu)

V projektu se vytvoří soubor *Dockerfile*, recept na vytvoření konečné image Dockeru. Informace o příkazech v souboru [Dockerfile](https://docs.docker.com/engine/reference/builder/) najdete v referenčních informacích.

Otevřete soubor *Dockerfile* v projektu a přidejte následující řádky pro instalaci Node.js 10.x v kontejneru. Nezapomeňte tyto řádky přidat jak v první části, tak pro přidání instalace správce balíčků Node *npm.exe* do základní image i do `build` části .

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

Soubor *Dockerfile* by teď měl vypadat nějak takhle:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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

Předchozí soubor *Dockerfile* je založený na [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image a obsahuje pokyny pro úpravu základní image sestavením projektu a jeho přidáním do kontejneru.

Když je zaškrtnuté políčko Konfigurovat pro **HTTPS** v dialogovém okně nového projektu, *soubor Dockerfile* zpřístupní dva porty. Jeden port se používá pro provoz HTTP. Druhý port se používá pro PROTOKOL HTTPS. Pokud políčko není zaškrtnuté, pro provoz HTTP se zobrazí jeden port (80).

## <a name="modify-the-dockerfile-windows-containers"></a>Úprava souboru Dockerfile (kontejnery Windows)

Dvojím kliknutím na uzel projektu otevřete soubor projektu a aktualizujte soubor projektu (*.csproj) přidáním následující vlastnosti jako podřízené vlastnosti `<PropertyGroup>` elementu:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aktualizujte soubor Dockerfile přidáním následujících řádků. Tím se do kontejneru zkopírují node a npm.

   1. Na ``# escape=` `` první řádek souboru Dockerfile přidejte .
   1. Před přidejte následující řádky. `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   2. Přidejte následující řádek před a za. `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   3. Úplný soubor Dockerfile by teď měl vypadat nějak takhle:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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

   4. Aktualizujte soubor .dockerignore odebráním `**/bin` .

## <a name="debug"></a>Ladění

V rozevíracím seznamu ladění na panelu nástrojů vyberte **Docker** a spusťte ladění aplikace. Může se zobrazit zpráva s výzvou o důvěřování certifikátu. Zvolte, že chcete certifikátu důvěřovat, aby pokračoval.  Při prvním sestavení docker stáhne základní image, takže to může trvat o něco déle.

Možnost **Nástroje kontejneru** v **okně Výstup** ukazuje, k jakým akcím došlo. Měli byste vidět kroky instalace související s *npm.exe*.

Prohlížeč zobrazí domovskou stránku aplikace.

::: moniker range="vs-2017"
   ![Snímek obrazovky se spuštěnou aplikací](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Snímek obrazovky se spuštěnou aplikací](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Zkuste převigovat na *stránku Čítač* a kliknutím na tlačítko **Increment** (Přírůstek) otestujte kód čítače na straně klienta.

Otevřete **konzolu Správce balíčků** (PMC) z nabídky **Nástroje**> NuGet Správce balíčků a **Správce balíčků konzoly.**

Výsledná image Dockeru aplikace je označená jako *dev*. Image je založená na *značce 3.1* základní image *dotnet/core/aspnet.* V `docker images` okně konzoly **Správce balíčků** (PMC) spusťte příkaz . Zobrazí se obrázky na počítači:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1                 e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> **Vývojová** image neobsahuje binární soubory aplikace a další  obsah, protože konfigurace ladění používají připojení svazku k zajištění iterativního prostředí pro úpravy a ladění. Pokud chcete vytvořit produkční image obsahující veškerý obsah, použijte **konfiguraci Vydání.**

V `docker ps` PMC spusťte příkaz . Všimněte si, že aplikace je spuštěná pomocí kontejneru:

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>Publikování imagí Dockeru

Po dokončení cyklu vývoje a ladění aplikace můžete vytvořit produkční image aplikace.

:::moniker range="vs-2017"

1. Změňte rozevírací seznam konfigurace na **Release (Verze)** a sestavte aplikaci.
1. Klikněte pravým tlačítkem na projekt **v Průzkumník řešení** a zvolte **Publikovat.**
1. V dialogovém okně cíl publikování vyberte **Container Registry**.
1. Zvolte **Vytvořit nový Azure Container Registry** a klikněte na **Publikovat.**
1. Do pole Create **a new (Vytvořit** nový) zadejte požadované Azure Container Registry .

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které chcete vytvořit registr kontejneru. Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění blízko vás | Zvolte Umístění v oblasti [ve vaší](https://azure.microsoft.com/regions/) blízkosti nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Visual Studio dialogového okna Azure Container Registry vytvoření](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. Vyberte **Vytvořit**.

   ![Snímek obrazovky znázorňující úspěšné publikování](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Změňte rozevírací seznam konfigurace na **Release (Verze)** a sestavte aplikaci.
1. Klikněte pravým tlačítkem na projekt **v Průzkumník řešení** a zvolte **Publikovat.**
1. V dialogovém okně cíl publikování vyberte **Docker Container Registry**.

   ![Zvolte Docker Container Registry](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Dále zvolte **Azure Container Registry**.

   ![Zvolte Azure Container Registry](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. Zvolte **Vytvořit nový Azure Container Registry**.
1. Na obrazovce Create **new Azure Container Registry vyplňte požadované** hodnoty.

    | Nastavení      | Navrhovaná hodnota  | Popis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Předpona DNS** | Globálně jedinečný název | Název, který jedinečně identifikuje váš registr kontejneru. |
    | **Předplatné** | Zvolte vaše předplatné. | Předplatné Azure, které se má použít. |
    | **[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Název skupiny prostředků, ve které chcete vytvořit registr kontejneru. Pokud chcete vytvořit novou skupinu prostředků, zvolte **Nová**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Úroveň služby registru kontejneru  |
    | **Umístění registru** | Umístění blízko vás | Zvolte Umístění v oblasti [ve vaší](https://azure.microsoft.com/regions/) blízkosti nebo v blízkosti jiných služeb, které budou používat váš registr kontejneru. |

    ![Visual Studio dialogového okna Azure Container Registry vytvoření](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. Vyberte **Vytvořit** a pak vyberte **Dokončit.**

   ![Výběr nebo vytvoření nové funkce ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   Po dokončení procesu publikování můžete zkontrolovat nastavení publikování a v případě potřeby je upravit nebo obrázek znovu publikovat pomocí **tlačítka Publikovat.**

   ![Snímek obrazovky znázorňující úspěšné publikování](media/container-tools-react/vs-2019/publish-finished.png)

   Pokud chcete znovu začít používat **dialogové okno** Publikovat, odstraňte profil publikování pomocí **odkazu Odstranit** na této stránce a pak znovu zvolte **Publikovat.**
:::moniker-end

## <a name="next-steps"></a>Další kroky

Kontejner teď můžete stáhnout z registru na libovolného hostitele, který dokáže spustit image Dockeru, například [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Další zdroje informací

* [Vývoj kontejnerů s Visual Studio](./index.yml)
* [Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru](troubleshooting-docker-errors.md)
* [Visual Studio úložiště Container Tools na GitHubu](https://github.com/Microsoft/DockerTools)

