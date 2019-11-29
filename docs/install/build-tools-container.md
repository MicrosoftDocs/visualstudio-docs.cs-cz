---
title: Instalace Visual Studio Build Tools do kontejneru
titleSuffix: ''
description: Naučte se, jak nainstalovat Visual Studio Build Tools do kontejneru Windows, aby se podporovaly pracovní postupy průběžné integrace a průběžného doručování (CI/CD).
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1d7c7ada277d9b9f7259b8ab07d93c48294b252c
ms.sourcegitcommit: 6336c387388707da94a91060dc3f34d4cfdc0a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74549967"
---
# <a name="install-build-tools-into-a-container"></a>Instalace nástrojů sestavení do kontejneru

Můžete nainstalovat Visual Studio Build Tools do kontejneru Windows, aby se podporovaly pracovní postupy průběžné integrace a průběžného doručování (CI/CD). Tento článek vás provede jednotlivými požadavky na konfiguraci Docker a také o tom, jaké [úlohy a součásti](workload-component-id-vs-build-tools.md) můžete v kontejneru nainstalovat.

[Kontejnery](https://www.docker.com/what-container) představují skvělý způsob, jak zabalit konzistentní systém sestavení, můžete použít nejen v prostředí serveru CI/CD, ale také pro vývojová prostředí. Svůj zdrojový kód můžete například připojit do kontejneru, aby jej bylo možné sestavit v přizpůsobeném prostředí, zatímco budete nadále používat aplikaci Visual Studio nebo jiné nástroje pro zápis kódu. Pokud váš pracovní postup CI/CD používá stejnou image kontejneru, můžete si být jisti, že se kód konzistentně vytváří. Kontejnery můžete použít také pro konzistenci za běhu, což je běžné pro mikroslužby, které používají více kontejnerů se systémem orchestrace. Nejedná se však o rámec tohoto článku.

Pokud Visual Studio Build Tools nemá pro sestavení zdrojového kódu k dispozici, můžete stejný postup použít pro jiné produkty sady Visual Studio. Upozorňujeme však, že kontejnery Windows nepodporují interaktivní uživatelské rozhraní, aby všechny příkazy musely být automatizované.

## <a name="before-you-begin"></a>Než začnete

Níže je popsána některá ze znalostí s [Docker](https://www.docker.com/what-docker) . Pokud ještě nejste obeznámeni se spouštěním Docker ve Windows, přečtěte si informace o tom, jak [nainstalovat a nakonfigurovat modul Docker ve Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

Základní image níže je ukázkou a nemusí fungovat pro váš systém. Pokud chcete zjistit, jakou základní image byste měli použít pro vaše prostředí, přečtěte si [kompatibilitu verzí kontejnerů Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) .

## <a name="create-and-build-the-dockerfile"></a>Vytvoření a sestavení souboru Dockerfile

Následující příklad souboru Dockerfile uložte do nového souboru na disku. Pokud je soubor pojmenován jednoduše "souboru Dockerfile", je ve výchozím nastavení rozpoznán.

> [!WARNING]
> Tento příklad souboru Dockerfile vyloučí jenom starší sady Windows SDK, které se nedají nainstalovat do kontejnerů. Starší verze způsobují selhání příkazu sestavení.

1. Otevřete příkazový řádek.

1. Vytvořit nový adresář (doporučeno):

   ```shell
   mkdir C:\BuildTools
   ```

1. Změňte adresáře do tohoto nového adresáře:

   ```shell
   cd C:\BuildTools
   ```

1. Uložit následující obsah do C:\BuildTools\Dockerfile.
 
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
   > Pokud jste image zavedli přímo na Microsoft/windowsservercore nebo mcr.microsoft.com/windows/servercore (viz téma [Microsoft syndikáting Container Catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)), .NET Framework nemusí být správně nainstalováno a nebude zobrazena žádná chyba instalace. Spravovaný kód se po dokončení instalace nemusí spustit. Místo toho použijte obrázek na bázi [Microsoft/DotNET-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Všimněte si také, že image s označením verze 4.7.2 nebo novější může jako výchozí `SHELL`používat PowerShell, což způsobí, že se `RUN` a pokyny `ENTRYPOINT` nezdařily.
   >
   > Visual Studio 2017 verze 15,8 nebo starší (jakýkoli produkt) nebude správně nainstalován v mcr.microsoft.com/windows/servercore:1809 nebo novějším. Nezobrazuje se žádná chyba.
   >
   > Informace o podporovaných verzích operačních systémů, ve kterých verzích operačního systému hostitele a [známých problémech pro kontejnery](build-tools-container-issues.md) pro známé problémy najdete v tématu [Kompatibilita verzí kontejnerů Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) .

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
   > Pokud bitovou kopii založíte přímo na Microsoft/windowsservercore, .NET Framework se nemusí správně nainstalovat a nebude se naznačit žádná chyba instalace. Spravovaný kód se po dokončení instalace nemusí spustit. Místo toho použijte obrázek na bázi [Microsoft/DotNET-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Všimněte si také, že image s označením verze 4,8 nebo novější můžou jako výchozí `SHELL`používat PowerShell, což způsobí, že se `RUN` a pokyny `ENTRYPOINT` nezdařily.
   >
   > Informace o podporovaných verzích operačních systémů, ve kterých verzích operačního systému hostitele a [známých problémech pro kontejnery](build-tools-container-issues.md) pro známé problémy najdete v tématu [Kompatibilita verzí kontejnerů Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) .

   ::: moniker-end
   
   > [!NOTE]
   > Kód chyby `3010` se používá k indikaci úspěšnosti s požadovaným restartováním. Další informace najdete v tématu [chybové zprávy programu Msiexec. exe](/windows/win32/msi/error-codes) .

1. V tomto adresáři spusťte následující příkaz.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Tento příkaz vytvoří souboru Dockerfile v aktuálním adresáři pomocí 2 GB paměti. Výchozí 1 GB není při instalaci některých úloh dostačující; v závislosti na požadavcích na sestavení však může být možné sestavení vytvořit pouze s 1 GB paměti.

   Konečný obrázek je označený jako "buildtools2017: nejnovější", takže ho můžete snadno spustit v kontejneru jako "buildtools2017", protože značka "poslední" je výchozí, pokud není zadaná žádná značka. Pokud chcete v pokročilejším [scénáři](advanced-build-tools-container.md)použít určitou verzi Visual Studio Build Tools 2017, můžete místo toho označit kontejner pomocí konkrétního čísla sestavení sady Visual Studio a také "poslední", aby kontejnery mohli používat konkrétní verzi konzistentně.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Tento příkaz vytvoří souboru Dockerfile v aktuálním adresáři pomocí 2 GB paměti. Výchozí 1 GB není při instalaci některých úloh dostačující; v závislosti na požadavcích na sestavení však může být možné sestavení vytvořit pouze s 1 GB paměti.

   Konečný obrázek je označený jako "buildtools2019: nejnovější", takže ho můžete snadno spustit v kontejneru jako "buildtools2019", protože značka "poslední" je výchozí, pokud není zadaná žádná značka. Pokud chcete v pokročilejším [scénáři](advanced-build-tools-container.md)použít určitou verzi Visual Studio Build Tools 2019, můžete místo toho označit kontejner pomocí konkrétního čísla sestavení sady Visual Studio a také "poslední", aby kontejnery mohli používat konkrétní verzi konzistentně.

   ::: moniker-end

## <a name="using-the-built-image"></a>Použití sestavené image

Teď, když jste vytvořili image, ji můžete spustit v kontejneru, abyste mohli provádět interaktivní i automatizované sestavení. V příkladu se používá Developer Command Prompt, takže vaše cesta a další proměnné prostředí jsou již nakonfigurovány.

1. Otevřete příkazový řádek.

1. Spusťte kontejner a spusťte prostředí PowerShell se sadou proměnných prostředí pro vývojáře:

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

Pokud chcete tuto image pro svůj pracovní postup CI/CD použít, můžete ji publikovat do vlastního [Azure Container Registry](https://azure.microsoft.com/services/container-registry) nebo jiného interního [registru Docker](https://docs.docker.com/registry/deploying) , aby se servery musely načíst jenom.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Rozšířený příklad pro kontejnery](advanced-build-tools-container.md)
* [Známé problémy s kontejnery](build-tools-container-issues.md)
* [Visual Studio Build Tools úlohy a ID komponent](workload-component-id-vs-build-tools.md)
