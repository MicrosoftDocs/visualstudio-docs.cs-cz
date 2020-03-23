---
title: Instalace nástrojů pro sestavení sady Visual Studio do kontejneru
titleSuffix: ''
description: Zjistěte, jak nainstalovat nástroje pro sestavení sady Visual Studio do kontejneru windows pro podporu průběžné integrace a nepřetržitého doručování (CI/CD).
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 53049d37f23a72adb337cdad629f4c689c83707e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114605"
---
# <a name="install-build-tools-into-a-container"></a>Instalace nástrojů sestavení do kontejneru

Nástroje pro sestavení sady Visual Studio můžete nainstalovat do kontejneru windows, abyste podpořili průběžné integrace a průběžné doručování (CI/CD). Tento článek vás provede tím, jaké změny konfigurace Dockeru jsou požadovány, a také jaké [úlohy a součásti](workload-component-id-vs-build-tools.md) můžete nainstalovat do kontejneru.

[Kontejnery](https://www.docker.com/what-container) jsou skvělý způsob, jak zabalit konzistentní sestavení systému můžete použít nejen v prostředí SERVERU CI/CD, ale pro vývojová prostředí stejně. Například můžete připojit zdrojový kód do kontejneru, který má být sestaven v přizpůsobeném prostředí, zatímco budete nadále používat Visual Studio nebo jiné nástroje k psaní kódu. Pokud váš pracovní postup CI/CD používá stejnou bitovou kopii kontejneru, můžete si být jisti, že váš kód sestaví konzistentně. Můžete použít kontejnery pro konzistenci za běhu také, což je běžné pro mikroslužby pomocí více kontejnerů s orchestrační systém; však je nad rámec tohoto článku.

Pokud nástroje pro sestavení sady Visual Studio nemají co potřebujete k vytvoření zdrojového kódu, lze tyto stejné kroky použít pro jiné produkty sady Visual Studio. Všimněte si však, že kontejnery systému Windows nepodporují interaktivní uživatelské rozhraní, takže všechny příkazy musí být automatizovány.

## <a name="before-you-begin"></a>Než začnete

Některé obeznámenost s [Docker](https://www.docker.com/what-docker) se předpokládá níže. Pokud ještě nejste obeznámeni se systémem Docker v systému Windows, přečtěte si o tom, jak [nainstalovat a nakonfigurovat modul Dockeru v systému Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

Základní obrázek níže je ukázka a nemusí fungovat pro váš systém. Chcete-li zjistit, kterou základní bitovou kopii byste měli použít pro své prostředí, přečtěte si [kompatibilitu verze kontejneru systému Windows.](/virtualization/windowscontainers/deploy-containers/version-compatibility)

## <a name="create-and-build-the-dockerfile"></a>Vytvoření a sestavení souboru Dockerfile

Uložte následující příklad Souboru Dockerfile do nového souboru na disku. Pokud je soubor pojmenován jednoduše "Dockerfile", je ve výchozím nastavení rozpoznán.

> [!WARNING]
> Tento příklad Dockerfile vylučuje pouze starší sady Windows SDK, které nelze nainstalovat do kontejnerů. Dřívější verze způsobit selhání příkazu sestavení.

1. Otevřete příkazový řádek.

1. Vytvoření nového adresáře (doporučeno):

   ```shell
   mkdir C:\BuildTools
   ```

1. Změna adresářů na tento nový adresář:

   ```shell
   cd C:\BuildTools
   ```

1. Uložte následující obsah do souboru C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Pokud bitovou kopii založíte přímo na microsoft/windowsservercore nebo mcr.microsoft.com/windows/servercore (viz [katalog kontejnerů syndikátorů společnosti Microsoft](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)), nemusí být rozhraní .NET Framework správně nainstalováno a není uvedena žádná chyba instalace. Spravovaný kód se nemusí spustit po dokončení instalace. Místo toho založte obrázek na [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Všimněte si také, že obrázky, které jsou označeny verze `SHELL`4.7.2 `RUN` `ENTRYPOINT` nebo novější může použít PowerShell jako výchozí , což způsobí, že a pokyny k selhání.
   >
   > Visual Studio 2017 verze 15.8 nebo starší (jakýkoli produkt) nebude správně nainstalovat na mcr.microsoft.com/windows/servercore:1809 nebo novější. Nezobrazí se žádná chyba.
   >
   > Kompatibilita verzí kontejneru windows a [zjistěte,](/virtualization/windowscontainers/deploy-containers/version-compatibility) které verze operačního systému kontejneru jsou podporovány na verzích hostitelského operačního systému a [známé problémy pro kontejnery](build-tools-container-issues.md) pro známé problémy.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Pokud bitovou kopii založíte přímo na microsoft/windowsservercore, rozhraní .NET Framework se nemusí správně nainstalovat a není uvedena žádná chyba instalace. Spravovaný kód se nemusí spustit po dokončení instalace. Místo toho založte obrázek na [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Všimněte si také, že obrázky, které jsou označeny `SHELL`verze 4.8 `RUN` `ENTRYPOINT` nebo novější může použít PowerShell jako výchozí , což způsobí, že a pokyny k selhání.
   >
   > Kompatibilita verzí kontejneru windows a [zjistěte,](/virtualization/windowscontainers/deploy-containers/version-compatibility) které verze operačního systému kontejneru jsou podporovány na verzích hostitelského operačního systému a [známé problémy pro kontejnery](build-tools-container-issues.md) pro známé problémy.

   ::: moniker-end
   
   > [!NOTE]
   > Kód `3010` chyby se používá k označení úspěchu s restartování [msiExec.exe chybové zprávy](/windows/win32/msi/error-codes) pro další informace.

1. V tomto adresáři spusťte následující příkaz.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Tento příkaz vytvoří Dockerfile v aktuálním adresáři pomocí 2 GB paměti. Výchozí 1 GB není dostatečná, pokud jsou nainstalovány některé úlohy; však může být možné sestavit pouze 1 GB paměti v závislosti na požadavcích sestavení.

   Konečný obrázek je označen "buildtools2017:latest", takže jej můžete snadno spustit v kontejneru jako "buildtools2017", protože "nejnovější" značka je výchozí, pokud není zadána žádná značka. Pokud chcete použít konkrétní verzi Visual Studio Sestavení nástroje 2017 v [pokročilejším scénáři](advanced-build-tools-container.md), můžete místo toho označit kontejner s konkrétní číslo sestavení Sady Visual Studio, stejně jako "nejnovější", takže kontejnery můžete používat konkrétní verzi konzistentně.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Tento příkaz vytvoří Dockerfile v aktuálním adresáři pomocí 2 GB paměti. Výchozí 1 GB není dostatečná, pokud jsou nainstalovány některé úlohy; však může být možné sestavit pouze 1 GB paměti v závislosti na požadavcích sestavení.

   Konečný obrázek je označen "buildtools2019:latest", takže jej můžete snadno spustit v kontejneru jako "buildtools2019", protože "nejnovější" značka je výchozí, pokud není zadána žádná značka. Pokud chcete použít konkrétní verzi Visual Studio Sestavení nástroje 2019 v [pokročilejším scénáři](advanced-build-tools-container.md), můžete místo toho označit kontejner s konkrétní číslo sestavení Sady Visual Studio, stejně jako "nejnovější", takže kontejnery můžete používat konkrétní verzi konzistentně.

   ::: moniker-end

## <a name="using-the-built-image"></a>Použití vytvořeného obrazu

Teď, když jste vytvořili bitovou kopii, můžete ji spustit v kontejneru a provést interaktivní i automatizovaná sestavení. Příklad používá příkazový řádek pro vývojáře, takže vaše cesta a další proměnné prostředí jsou již nakonfigurovány.

1. Otevřete příkazový řádek.

1. Spuštěním kontejneru spustíte prostředí Prostředí PowerShell se všemi nastavenými proměnnými prostředí pro vývojáře:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Chcete-li tuto bitovou kopii použít pro pracovní postup CI/CD, můžete ji publikovat do vlastního [registru kontejnerů Azure](https://azure.microsoft.com/services/container-registry) nebo do jiného interního [registru Dockeru,](https://docs.docker.com/registry/deploying) takže servery je potřeba pouze k jeho vyhledání.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Rozšířený příklad pro kontejnery](advanced-build-tools-container.md)
* [Známé problémy s kontejnery](build-tools-container-issues.md)
* [Úlohy a ID součástí nástrojů sady Visual Studio](workload-component-id-vs-build-tools.md)
