---
title: Nainstalovat Visual Studio Build Tools do kontejneru
titleSuffix: ''
description: Zjistěte, jak nainstalovat Visual Studio Build Tools do kontejneru Windows pro podporu kontinuální integrace a pracovní postupy průběžné doručování (CI/CD).
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdb7148560dfca966b82d8d9cef617075752a58b
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307700"
---
# <a name="install-build-tools-into-a-container"></a>Instalace Build Tools do kontejneru

Visual Studio Build Tools můžete nainstalovat do kontejneru Windows pro podporu kontinuální integrace a pracovní postupy průběžné doručování (CI/CD). Tento článek vás provede změny konfigurace Dockeru se vyžadují i co [úlohy a komponenty](workload-component-id-vs-build-tools.md) můžete nainstalovat v kontejneru.

[Kontejnery](https://www.docker.com/what-container) jsou skvělý způsob, jak systém konzistentní sestavení, můžete použít pouze v prostředí s CI/CD servery, ale pro vývojové prostředí a balíčků. Například můžete připojit váš zdrojový kód do kontejneru, který má být sestaven přizpůsobené prostředí. když budete pokračovat v používání sady Visual Studio nebo jinými nástroji psát kód. Pokud váš pracovní postup CI/CD používá stejnou image kontejneru, máte jistotu, které se kód sestavil konzistentně. Kontejnery můžete použít pro modul runtime konzistence, což je běžné, že mikroslužby pomocí systému Orchestrace; více kontejnerů je ale nad rámec tohoto článku.

Pokud Visual Studio Build Tools neobsahuje nezbytné k sestavování zdrojového kódu, stejný postup lze použít pro produkty Visual Studio. Mějte na paměti, ale kontejnerů Windows, je potřeba automatizovat všechny příkazy nepodporují interaktivní uživatelské rozhraní.

## <a name="overview"></a>Přehled

Pomocí [Docker](https://www.docker.com/what-docker) vytvořit image ze kterého můžete vytvořit kontejnery, které sestavení zdrojového kódu. Příklad souboru Dockerfile nainstaluje nejnovější sadu Visual Studio vytvářet nástroje 2017 a některé další užitečné programy často používají pro sestavování zdrojového kódu. Můžete dále upravit vlastní soubor Dockerfile zahrnout další nástroje a skripty pro spuštění testů, publikování výstupu sestavení a další.

Pokud jste již nainstalovali Docker pro Windows, můžete přeskočit ke kroku 3.

## <a name="step-1-enable-hyper-v"></a>Krok 1. Povolení role Hyper-V

Technologie Hyper-V není povolena ve výchozím nastavení. Musí být povolené spuštění Docker pro Windows, od aktuálně je podporována pouze izolace Hyper-V pro Windows 10.

* [Povolení technologie Hyper-V ve Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Povolení Hyper-V ve Windows serveru 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> Na počítači musí být povolena virtualizace. Obvykle je ve výchozím nastavení; povolené ale pokud se nepovede instalaci technologie Hyper-V, naleznete v dokumentaci k systému pro povolení virtualizace.

## <a name="step-2-install-docker-for-windows"></a>Krok 2. Nainstalovat Docker for Windows

Pokud používáte Windows 10, můžete si [stáhnout a nainstalovat Docker Community Edition](https://docs.docker.com/docker-for-windows/install). Pokud používáte Windows Server 2016, postupujte podle [pokynů a nainstalujte Docker Enterprise Edition](https://docs.docker.com/install/windows/docker-ee).

## <a name="step-3-switch-to-windows-containers"></a>Krok 3. Přepnout na Windows kontejnery

Sestavení nástroje 2017 můžete nainstalovat jenom na Windows, který vyžaduje, abyste [přepnout na kontejnery Windows](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Kontejnery Windows ve Windows 10 podporují pouze [izolace Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), ale kontejnerů Windows ve Windows serveru 2016 podporují Hyper-V a izolace procesů.

## <a name="step-4-expand-maximum-container-disk-size"></a>Krok 4. Rozbalte kontejner maximální velikost disku

Visual Studio Build Tools - a ve větší míře, Visual Studio – vyžadují velké množství místa na disku pro všechny nástroje, které se nainstalují. I v případě, že v příkladu soubor Dockerfile zakáže mezipaměť balíčků, velikost disku imagí kontejnerů musí být skutečnost zohlednit zvýšením požadované místo. Momentálně na Windows, můžete pouze zvýšit velikost disku tak, že změníte konfiguraci Dockeru.

**Ve Windows 10**:

1. [Klikněte pravým tlačítkem na ikonu Dockeru pro Windows](https://docs.docker.com/docker-for-windows/#docker-settings) na hlavním panelu a klikněte na **nastavení**.
2. [Klikněte na proces démon](https://docs.docker.com/docker-for-windows/#docker-daemon) oddílu.
3. [Přepnout **základní** ](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) tlačítko **Upřesnit**.
4. Přidejte následující pole vlastnost JSON zvětšete místo na disku na 120 GB (víc než dost pro Build Tools se místo pro růst).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Tato vlastnost se přidá do všechno, co už máte. Například se tyto změny se použily výchozí konfigurační soubor démon, měli byste vidět:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Klikněte na tlačítko **použít**.

**V systému Windows Server 2016**:

1. Zastavte službu "docker":

   ```shell
   sc.exe stop docker
   ```

2. Z příkazového řádku se zvýšenými oprávněními upravit "% ProgramData%\Docker\config\daemon.json" (nebo cokoli, co jste zadali pro `dockerd --config-file`).
3. Přidejte následující pole vlastnost JSON zvětšete místo na disku na 120 GB (víc než dost pro Build Tools se místo pro růst).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Tato vlastnost se přidá do všechno, co už máte.
4. Soubor uložte a zavřete.
5. Spusťte službu "docker":

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Krok 5. Vytvoření a vytvoření souboru Dockerfile

Uložte soubor Dockerfile v následujícím příkladu do nového souboru na disku. Pokud je soubor nazván jednoduše soubor Dockerfile"", je rozpoznán ve výchozím nastavení.

> [!WARNING]
> V tomto příkladu soubor Dockerfile pouze vyloučí starší Windows SDK, kterou nejde instalovat do kontejnerů. Dřívější verze způsobit selhání příkazu sestavení.

1. Otevřete příkazový řádek.
2. Vytvořte nový adresář (doporučeno):

   ```shell
   mkdir C:\BuildTools
   ```

3. Změňte adresář na tento nový adresář:

   ```shell
   cd C:\BuildTools
   ```

3. Uložte C:\BuildTools\Dockerfile následujícím obsahem.

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
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
   > Pokud vytváříte svou image přímo na microsoft/windowsservercore, nemusí správně nainstalovat rozhraní .NET Framework a je uvedena žádná chyba instalace. Po dokončení instalace se možná nespustí spravovaný kód. Místo toho na základní image [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Také Upozorňujeme, že Image označené verze 4.7.1 nebo vyšší může pomocí prostředí PowerShell jako výchozí `SHELL` bude `RUN` a `ENTRYPOINT` pokyny k selhání.
   >
   > Visual Studio 2017 verze 15,8 nebo starší (libovolný produkt) nenainstaluje správně mcr<span></span>.microsoft\.com\/windows\/servercore:1809 nebo novější. Se nezobrazí žádná chyba.
   >
   > Zobrazit [známé problémy pro kontejnery](build-tools-container-issues.md) Další informace.

4. Spusťte následující příkaz v tomto adresáři.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Tento příkaz sestaví soubor Dockerfile v aktuálním adresáři pomocí 2 GB paměti. Výchozí hodnota 1 GB nestačí při instalaci některých úloh; však může být možné sestavit pouze 1 GB paměti, v závislosti na požadavcích sestavení.

   Finální image je označený "buildtools2017:latest", takže můžete snadno ji spustit v kontejneru jako "buildtools2017" od "posledního" značka je výchozí, pokud není zadána žádná značka. Pokud chcete použít konkrétní verzi sady Visual Studio vytvářet 2017 nástroje více [pokročilý scénář](advanced-build-tools-container.md), může být místo toho značku kontejneru s konkrétním Visual Studio build číslo stejně jako "posledního", tak kontejnery lze použít konkrétní verze konzistentně.

## <a name="step-6-using-the-built-image"></a>Krok 6. Pomocí sestavenou image

Teď, když jste vytvořili image, můžete ji spustit v kontejneru provádět interaktivní a automatizované sestavování. V příkladu se používá Developer Command Prompt, takže vaše cesta i ostatním proměnným prostředí jsou už nakonfigurovaná.

1. Otevřete příkazový řádek.
2. Spuštění kontejneru začínat prostředí PowerShell pro všechny vývojáře nastavení proměnné prostředí:

   ```shell
   docker run -it buildtools2017
   ```

Pokud chcete použít tuto bitovou kopii pro pracovní postup CI/CD, je možné ji publikovat na vlastní [Azure Container Registry](https://azure.microsoft.com/services/container-registry) nebo jiných interní [registru Dockeru](https://docs.docker.com/registry/deploying) tak servery stačí stáhnout.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Rozšířený příklad pro kontejnery](advanced-build-tools-container.md)
* [Známé problémy s kontejnery](build-tools-container-issues.md)
* [ID pracovního vytížení a komponenta Visual Studio 2017 nástroje sestavení](workload-component-id-vs-build-tools.md)
