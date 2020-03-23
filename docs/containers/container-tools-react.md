---
title: Nástroje kontejnerů visual studia s ASP.NET core a react.js
author: ghogen
description: Přečtěte si, jak používat nástroje pro kontejnery Visual Studio a Docker pro Windows
ms.author: ghogen
ms.date: 10/16/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: af859c1c06820aa477869f6968e9c652bd525de6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916739"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Úvodní příručka: Použití Dockeru s jednostránkovou aplikací React v Sadě Visual Studio

Pomocí Visual Studia můžete snadno vytvářet, ladit a spouštět kontejnerizované aplikace ASP.NET Core, včetně aplikací s javascriptem na straně klienta, jako je jednostránková aplikace React.js, a publikovat je do registru kontejnerů Azure (ACR), Docker Hubu, Služby Azure App Service nebo vlastních aplikací registru kontejnerů. V tomto článku budeme publikovat do ACR.

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core pro vývoj napříč platformami**
* Chcete-li publikovat do registru kontejnerů Azure, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Pro kontejnery Windows windows 10 verze 1903 nebo novější, chcete-li použít imbliny Dockeru uvedené v tomto článku.
::: moniker-end
::: moniker range=">=vs-2019"
* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core**
* [.NET Core 2.2 Vývojové nástroje](https://dotnet.microsoft.com/download/dotnet-core/2.2) pro vývoj s .NET Core 2.2
* Chcete-li publikovat do registru kontejnerů Azure, předplatné Azure. [Zaregistrujte si bezplatnou zkušební verzi](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Pro kontejnery Windows windows 10 verze 1903 nebo novější, chcete-li použít imbliny Dockeru uvedené v tomto článku.
::: moniker-end

## <a name="installation-and-setup"></a>Instalace a nastavení

V případě instalace Dockeru nejprve zkontrolujte informace na [ploše Dockeru pro Windows: Co je třeba vědět před instalací](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Dále nainstalujte [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Vytvoření projektu a přidání podpory Dockeru

::: moniker range="vs-2017"
1. Vytvořte nový projekt pomocí šablony **ASP.NET základní webové aplikace.**
1. Vyberte **možnost React.js**. Nemůžete vybrat **Povolit podporu Dockeru**, ale nebojte se, tuto podporu můžete přidat po vytvoření projektu.

   ![Snímek obrazovky s novým projektem React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Klikněte pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **podporu Dockeru** pro přidání souboru Dockerfile do projektu.

   ![Přidání podpory Dockeru](media/container-tools-react/vs2017/add-docker-support.png)

1. Vyberte typ kontejneru a klepněte na **tlačítko OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Vytvořte nový projekt pomocí šablony **ASP.NET základní webové aplikace.**
1. Vyberte **React.js**a klepněte na **vytvořit**. Nemůžete vybrat **Povolit podporu Dockeru**, ale nebojte se, můžete tuto podporu přidat později.

   ![Snímek obrazovky s novým projektem React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Klikněte pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **podporu Dockeru** pro přidání souboru Dockerfile do projektu.

   ![Přidání podpory Dockeru](media/container-tools-react/vs2017/add-docker-support.png)

1. Vyberte typ kontejneru.
::: moniker-end

Dalším krokem je rozdíl v závislosti na tom, zda používáte linuxové kontejnery nebo kontejnery windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Úprava souboru Dockerfile (linuxové kontejnery)

*Dockerfile*, recept pro vytvoření konečné image Dockeru, je vytvořen v projektu. Odkazovat na [odkaz Dockerfile](https://docs.docker.com/engine/reference/builder/) pro pochopení příkazů v něm.

Otevřete *dockerfile* v projektu a přidejte následující řádky pro instalaci Node.js 10.x v kontejneru. Nezapomeňte přidat tyto řádky v první části, chcete-li přidat instalaci správce balíčků uzlu *npm.exe* do základní bitové kopie, která se používá v následujících krocích.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile* by nyní měl vypadat nějak takto:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
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

Předchozí *soubor Dockerfile* je založen na image [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) a obsahuje pokyny pro úpravu základní bitové kopie vytvořením projektu a jeho přidáním do kontejneru.

Když je zaškrtnuto políčko **Konfigurovat pro protokol HTTPS** nového dialogového okna projektu, *dockerfile* zpřístupní dva porty. Jeden port se používá pro přenosy HTTP; druhý port se používá pro protokol HTTPS. Pokud políčko není zaškrtnuto, jeden port (80) je vystaven pro přenosy HTTP.

## <a name="modify-the-dockerfile-windows-containers"></a>Úprava souboru Dockerfile (kontejnery Windows)

Otevřete soubor projektu poklepáním na uzel projektu a aktualizujte soubor projektu (*.csproj) přidáním `<PropertyGroup>` následující vlastnosti jako podřízeného prvku:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aktualizujte soubor Dockerfile přidáním následujících řádků. Tím zkopírujete uzel a npm do kontejneru.

   1. Přidat ``# escape=` `` do prvního řádku Dockerfile
   1. Před následující řádky přidejte následující řádky`FROM … base`

      ```
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Přidejte následující řádek před a za`FROM … build`

      ```
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Kompletní Dockerfile by nyní měl vypadat nějak takto:

      ```
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      RUN Expand-Archive nodejs.zip -DestinationPath C:\; `
      RUN Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

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

1. Aktualizujte soubor .dockerignore `**/bin`odebráním souboru .

## <a name="debug"></a>Ladění

Vyberte **Docker** z rozevíracího okna ladění na panelu nástrojů a začněte ladit aplikaci. Může se zobrazit zpráva s výzvou k důvěře certifikátu. zvolte důvěřovat certifikátu, aby mohl pokračovat.  Při prvním sestavení docker stáhne základní bitové kopie, takže to může trvat o něco déle.

Možnost **Nástroje kontejneru** v okně **Výstup** ukazuje, jaké akce probíhají. Měli byste vidět kroky instalace spojené s *npm.exe*.

V prohlížeči se zobrazí domovská stránka aplikace.

::: moniker range="vs-2017"
   ![Snímek obrazovky se spuštěnou aplikací](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Snímek obrazovky se spuštěnou aplikací](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Zkuste přecházet na stránku *Čítač* a otestujte kód čítače na straně klienta klepnutím na tlačítko **Přírůstek.**

Otevřete **konzolu Správce balíčků** (PMC) v nabídce **Nástroje**> Správce balíčků NuGet, **konzola správce balíčků**.

Výsledná image Dockeru aplikace je označena jako *dev*. Obrázek je založen na značce *2.2-aspnetcore-runtime* základní bitové kopie *microsoft/dotnet.* Spusťte `docker images` příkaz v okně **Konzola správce balíčků** (PMC). Obrázky na zařízení jsou zobrazeny:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Obrázek dev** neobsahuje binární soubory aplikace a další obsah, protože konfigurace **ladění** používají připojení svazku k zajištění iterativního prostředí pro úpravy a ladění. Chcete-li vytvořit produkční bitovou kopii obsahující veškerý obsah, použijte konfiguraci **vydání.**

Spusťte `docker ps` příkaz v PMC. Všimněte si, že aplikace běží pomocí kontejneru:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
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

1. Klikněte na **Vytvořit**.

   ![Snímek obrazovky s úspěšným publikováním](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Další kroky

Nyní můžete vytáhnout kontejner z registru na libovolného hostitele schopného spouštět ibi Dockeru, například [instance kontejneru Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Další zdroje

* [Vývoj kontejnerů pomocí sady Visual Studio](/visualstudio/containers)
* [Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru](troubleshooting-docker-errors.md)
* [Úložiště GitHub nástrojů kontejneru Visual Studia](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end