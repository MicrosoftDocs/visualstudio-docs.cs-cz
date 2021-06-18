---
title: Instalace Visual Studio Build Tools do kontejneru
titleSuffix: ''
description: Zjistěte, jak nainstalovat Visual Studio Build Tools do kontejneru Windows pro podporu pracovních postupů kontinuální integrace a průběžného doručování (CI/CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e29e780d146fec63bc1375ed16f72067f9b4ccee
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307632"
---
# <a name="install-build-tools-into-a-container"></a>Instalace nástrojů buildu do kontejneru

Můžete je nainstalovat Visual Studio Build Tools do kontejneru Windows pro podporu pracovních postupů kontinuální integrace a průběžného doručování (CI/CD). Tento článek vás provede změnami konfigurace Dockeru [](workload-component-id-vs-build-tools.md) a také úlohami a komponentami, které můžete do kontejneru nainstalovat.

[Kontejnery](https://www.docker.com/what-container) jsou skvělým způsobem, jak zabalovat konzistentní systém sestavení, který můžete použít nejen v serverových prostředích CI/CD, ale i pro vývojová prostředí. Můžete například připojit zdrojový kód ke kontejneru, který se má vytvořit pomocí přizpůsobeného prostředí, a přitom k psaní kódu používat Visual Studio nebo jiné nástroje. Pokud pracovní postup CI/CD používá stejnou image kontejneru, můžete si být jistí, že se kód konzistentně sestavuje. Kontejnery můžete použít také pro konzistenci modulu runtime, což je běžné u mikroslužb, které používají více kontejnerů se systémem orchestrace. je však nad rámec tohoto článku.

Pokud Visual Studio Build Tools to, co k vytvoření zdrojového kódu potřebujete, můžete stejný postup použít i pro jiné Visual Studio produkty. Nezapomeňte ale, že kontejnery Windows nepodporují interaktivní uživatelské rozhraní, takže všechny příkazy musí být automatizované.

## <a name="before-you-begin"></a>Než začnete

Předpokládá se následující znalost [Dockeru.](https://www.docker.com/what-docker) Pokud ještě nejste obeznámeni se spuštěním Dockeru ve Windows, přečtěte si, jak nainstalovat a nakonfigurovat modul [Docker ve Windows.](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)

Základní image níže je ukázková a nemusí pro váš systém fungovat. Přečtěte [si informace o kompatibilitě verzí kontejneru Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) a zjistěte, kterou základní image byste měli použít pro vaše prostředí.

## <a name="create-and-build-the-dockerfile"></a>Vytvoření a sestavení souboru Dockerfile

Uložte následující příklad souboru Dockerfile do nového souboru na disku. Pokud má soubor název jednoduše "Dockerfile", ve výchozím nastavení se rozpozná.

> [!WARNING]
> Tento příklad dockerfile vyloučí jenom starší verze windows SDK, které nelze nainstalovat do kontejnerů. Dřívější verze způsobí selhání příkazu sestavení.

1. Otevřete příkazový řádek.

1. Vytvořte nový adresář (doporučeno):

   ```shell
   mkdir C:\BuildTools
   ```

1. Změňte adresáře na tento nový adresář:

   ```shell
   cd C:\BuildTools
   ```

1. Uložte následující obsah do složky C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/15/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache `
           --installPath C:\BuildTools `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Seznam úloh a komponent najdete v adresáři Visual Studio Build Tools [komponent.](workload-component-id-vs-build-tools.md)
   >

   > [!WARNING]
   > Pokud svou image založte přímo na microsoft/windowsservercore nebo mcr.microsoft.com/windows/servercore (viz Katalog kontejnerů [syndikáty Microsoftu),](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)nemusí se .NET Framework správně nainstalovat a není označena žádná chyba instalace. Spravovaný kód se po dokončení instalace nemusí spustit. Místo toho svou image založit na [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novějším. Všimněte si také, že image se značkou verze 4.7.2 nebo novější můžou jako výchozí používat PowerShell, což způsobí selhání pokynů a `SHELL` `RUN` `ENTRYPOINT` .
   >
   > Visual Studio 2017 verze 15.8 nebo starší (žádný produkt) se správně nenainstaluje na mcr.microsoft.com/windows/servercore:1809 nebo novější. Nezobrazí se žádná chyba.
   >
   > Informace [o tom,](/virtualization/windowscontainers/deploy-containers/version-compatibility) které verze operačního systému kontejneru podporují [](build-tools-container-issues.md) verze hostitelských operačních systémů, a Známé problémy s kontejnery pro známé problémy, najdete v tématu Kompatibilita verzí kontejneru Windows.
   
   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/16/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache modify `
           --installPath "%ProgramFiles(x86)%\Microsoft Visual Studio\2019\BuildTools" `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Seznam úloh a komponent najdete v adresáři Visual Studio Build Tools [komponent.](workload-component-id-vs-build-tools.md)
   >

   > [!WARNING]
   > Pokud svou image založte přímo na virtuálním počítači microsoft/windowsservercore, .NET Framework se nemusí správně nainstalovat a není označena žádná chyba instalace. Spravovaný kód se po dokončení instalace nemusí spustit. Místo toho svou image založit na [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novějším. Všimněte si také, že image se značkou verze 4.8 nebo novější můžou jako výchozí používat PowerShell, což způsobí selhání `SHELL` `RUN` pokynů a `ENTRYPOINT` .
   >
   > Informace [o tom,](/virtualization/windowscontainers/deploy-containers/version-compatibility) které verze operačního systému kontejneru podporují [](build-tools-container-issues.md) verze hostitelských operačních systémů, a Známé problémy s kontejnery pro známé problémy, najdete v tématu Kompatibilita verzí kontejneru Windows.

   ::: moniker-end
   
   > [!NOTE]
   > Kód chyby `3010` slouží k označení úspěchu s požadovaným restartováním. Další informaceMsiExec.exe [ v](/windows/win32/msi/error-codes) části Chybové zprávy.

1. V tomto adresáři spusťte následující příkaz.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Tento příkaz sestaví soubor Dockerfile v aktuálním adresáři s použitím 2 GB paměti. Výchozí 1 GB při instalaci některých úloh nestačí. V závislosti na vašich požadavcích na sestavení ale můžete být schopni sestavovat pouze s 1 GB paměti.

   Konečná image je označená jako buildtools2017:latest, takže ji můžete snadno spustit v kontejneru jako buildtools2017, protože pokud není zadána žádná značka, je výchozí značka "latest". Pokud chcete použít konkrétní verzi Visual Studio Build Tools 2017 v pokročilejším scénáři [,](advanced-build-tools-container.md)můžete místo toho kontejner označit konkrétním číslem sestavení Visual Studio a také nejnovější verzí, aby kontejnery mohly konzistentně používat konkrétní verzi.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Tento příkaz sestaví soubor Dockerfile v aktuálním adresáři s použitím 2 GB paměti. Výchozí 1 GB při instalaci některých úloh nestačí. V závislosti na vašich požadavcích na sestavení ale můžete být schopni sestavovat pouze s 1 GB paměti.

   Konečná image je označená jako buildtools2019:latest, takže ji můžete snadno spustit v kontejneru jako buildtools2019, protože pokud není zadána žádná značka, je výchozí značka "latest". Pokud chcete použít konkrétní verzi Visual Studio Build Tools 2019 v pokročilejším [scénáři,](advanced-build-tools-container.md)můžete místo toho kontejner označit konkrétním číslem sestavení Visual Studio a také nejnovější verzí, aby kontejnery mohly konzistentně používat konkrétní verzi.

   ::: moniker-end

## <a name="using-the-built-image"></a>Použití sestavené image

Teď, když jste vytvořili image, ji můžete spustit v kontejneru a provést interaktivní i automatizované sestavení. V příkladu se používá Developer Command Prompt, takže cesta a další proměnné prostředí jsou už nakonfigurované.

1. Otevřete příkazový řádek.

1. Spuštěním kontejneru spusťte prostředí PowerShell se všemi nastavenými proměnnými prostředí pro vývojáře:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Pokud chcete tuto image použít pro pracovní postup CI/CD, můžete ji publikovat do vlastního [Azure Container Registry](https://azure.microsoft.com/services/container-registry) nebo jiného interního registru [Dockeru,](https://docs.docker.com/registry/deploying) takže je servery potřebují jenom vyžádat.

   > [!NOTE]
   > Pokud se kontejner Dockeru nepodaří spustit, pravděpodobně dojde k Visual Studio problému s instalací. Soubor Dockerfile můžete aktualizovat a odebrat tak krok, který volá Visual Studio batch. To vám umožní spustit kontejner Dockeru a přečíst si protokoly chyb instalace.
   >
   > V souboru Dockerfile odeberte z `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` příkazu parametry a `ENTRYPOINT` . Příkaz by teď měl být `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` . Dále znovu sestavte soubor Dockerfile a spusťte příkaz `run` pro přístup k souborům kontejneru. Pokud chcete najít protokoly chyb instalace, přejděte do `$env:TEMP` adresáře a vyhledejte `dd_setup_<timestamp>_errors.log` soubor .
   >
   > Po identifikaci a opravě problému s instalací můžete přidat parametry a zpět do příkazu a znovu `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` sestavit soubor `ENTRYPOINT` Dockerfile.
   >
   > Další informace najdete v tématu [Známé problémy pro kontejnery.](build-tools-container-issues.md)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Rozšířený příklad pro kontejnery](advanced-build-tools-container.md)
* [Známé problémy s kontejnery](build-tools-container-issues.md)
* [Visual Studio Build Tools ID úloh a komponent](workload-component-id-vs-build-tools.md)
