---
title: Pokročilý příklad pro kontejnery
description: ''
ms.date: 07/03/2019
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0a88815c4a2853270b539a3e012297b681af62e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114953"
---
# <a name="advanced-example-for-containers"></a>Pokročilý příklad pro kontejnery

::: moniker range="vs-2017"

Ukázkový soubor Dockerfile v [aplikaci Install Build Tools do kontejneru](build-tools-container.md) vždy používá bitovou kopii [Microsoft/Dotnet-Framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) založenou na nejnovější bitové kopii Microsoft/WindowsServercore a nejnovější instalační službě Nástrojů pro sestavení sady Visual Studio. Pokud publikujete tuto bitovou kopii do [registru Dockeru](https://azure.microsoft.com/services/container-registry) pro ostatní, aby ji mohli vyžádat, může být tato bitová kopie v pořádku pro mnoho scénářů. V praxi je však běžnější být konkrétní ohledně toho, jakou základní bitovou kopii používáte, jaké binární soubory stáhnete a jaké verze nástrojů nainstalujete.

::: moniker-end

::: moniker range="vs-2019"

Ukázkový soubor Dockerfile v [aplikaci Install Build Tools do kontejneru](build-tools-container.md) vždy používá bitovou kopii [Microsoft/Dotnet-Framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) založenou na nejnovější bitové kopii Microsoft/WindowsServercore a nejnovější instalační službě nástrojů sady Visual Studio. Pokud publikujete tuto bitovou kopii do [registru Dockeru](https://azure.microsoft.com/services/container-registry) pro ostatní, aby ji mohli vyžádat, může být tato bitová kopie v pořádku pro mnoho scénářů. V praxi je však běžnější být konkrétní ohledně toho, jakou základní bitovou kopii používáte, jaké binární soubory stáhnete a jaké verze nástrojů nainstalujete.

::: moniker-end

Následující příklad Dockerfile používá konkrétní značku verze image microsoft/dotnet-Framework. Použití konkrétní značky pro základní obrázek je samozřejmostí a usnadňuje zapamatování, že vytváření nebo opětovné sestavení obrázků má vždy stejný základ.

> [!NOTE]
> Sadu Visual Studio nelze nainstalovat do aplikace Microsoft/windowsservercore:10.0.14393.1593 ani do libovolné bitové kopie, která je na něm založena, což má známé problémy se spuštěním instalačního programu v kontejneru. Další informace naleznete v [tématu Známé problémy pro kontejnery](build-tools-container-issues.md).

Následující příklad stáhne nejnovější verzi nástroje pro sestavení. Pokud chcete použít starší verzi nástroje sestavení, které můžete nainstalovat do kontejneru později, musíte nejprve [vytvořit](create-an-offline-installation-of-visual-studio.md) a [udržovat](update-a-network-installation-of-visual-studio.md) rozložení.

## <a name="install-script"></a>Nainstalovat skript

Chcete-li shromažďovat protokoly při výskytu chyby instalace, vytvořte v pracovním adresáři dávkový skript s názvem Install.cmd, který obsahuje následující obsah:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Soubor dockeru

V pracovním adresáři vytvořte "Dockerfile" s následujícím obsahem:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 verze 15.8 nebo starší (jakýkoli produkt)\.\/se\/nebude správně instalovat na mcr\.microsoft com windows servercore:1809 nebo novější. Nezobrazí se žádná chyba.
   >
   > Další informace naleznete [v tématu Známé problémy pro kontejnery.](build-tools-container-issues.md)

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Chcete-li vytvořit bitovou kopii v aktuálním pracovním adresáři, spusťte následující příkaz:

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

Volitelně předat buď `FROM_IMAGE` `CHANNEL_URL` nebo oba `--build-arg` nebo argumenty pomocí přepínače příkazového řádku určit jiný základní obraz nebo umístění vnitřní rozložení zachovat pevný obraz.

## <a name="diagnosing-install-failures"></a>Diagnostika selhání instalace

Tento příklad stáhne konkrétní nástroje a ověří, že se shody hodnot hash. Také stáhne nejnovější Visual Studio a .NET kolekce protokolu nástroj tak, aby v případě selhání instalace dojde, můžete zkopírovat protokoly do hostitelského počítače analyzovat selhání.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Po dokončení posledního řádku otevřete v počítači stránku %TEMP%\vslogs.zip nebo odešlete problém na webu [komunity vývojářů.](https://developercommunity.visualstudio.com)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace Build Tools do kontejneru](build-tools-container.md)
* [Známé problémy s kontejnery](build-tools-container-issues.md)
* [Úlohy a ID součástí nástrojů sady Visual Studio](workload-component-id-vs-build-tools.md)
