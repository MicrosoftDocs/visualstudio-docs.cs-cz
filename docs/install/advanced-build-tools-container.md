---
title: Rozšířený příklad pro kontejnery
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114953"
---
# <a name="advanced-example-for-containers"></a>Rozšířený příklad pro kontejnery

::: moniker range="vs-2017"

Vzorový souboru Dockerfile při [instalaci nástrojů sestavení do kontejneru](build-tools-container.md) vždy používá Image [Microsoft/DotNET-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) na základě nejnovější image Microsoft/windowsservercore a nejnovější instalační službu Visual Studio Build Tools. Pokud tuto image publikujete do [registru Docker](https://azure.microsoft.com/services/container-registry) , aby ji ostatní mohli vyžádat, může být tato image v mnoha scénářích v pořádku. V praxi je ale běžnější, že se jedná o konkrétní základní image, jaké binární soubory stáhnete a které verze nástrojů nainstalujete.

::: moniker-end

::: moniker range="vs-2019"

Vzorový souboru Dockerfile při [instalaci nástrojů sestavení do kontejneru](build-tools-container.md) vždy používá Image [Microsoft/DotNET-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) na základě nejnovější image Microsoft/windowsservercore a nejnovější instalační službu Visual Studio Build Tools. Pokud tuto image publikujete do [registru Docker](https://azure.microsoft.com/services/container-registry) , aby ji ostatní mohli vyžádat, může být tato image v mnoha scénářích v pořádku. V praxi je ale běžnější, že se jedná o konkrétní základní image, jaké binární soubory stáhnete a které verze nástrojů nainstalujete.

::: moniker-end

Následující příklad souboru Dockerfile používá specifickou značku verze image Microsoft/DotNET-Framework. Použití konkrétní značky pro základní Image je maloobchodech a usnadňuje zapamatování, že vytváření a obnovování imagí má vždycky stejný základ.

> [!NOTE]
> Visual Studio nemůžete nainstalovat do Microsoft/windowsservercore: 10.0.14393.1593 ani do žádné image na nich založené, která má známé problémy při spouštění instalačního programu v kontejneru. Další informace najdete v tématu [známé problémy pro kontejnery](build-tools-container-issues.md).

Následující příklad stáhne nejnovější vydání nástrojů buildu. Chcete-li použít starší verzi nástrojů sestavení, které lze nainstalovat do kontejneru později, je nutné nejprve [vytvořit](create-an-offline-installation-of-visual-studio.md) a [udržovat](update-a-network-installation-of-visual-studio.md) rozložení.

## <a name="install-script"></a>Nainstalovat skript

Pokud chcete shromažďovat protokoly, když dojde k chybě instalace, vytvořte v pracovním adresáři dávkový skript s názvem Install. cmd, který obsahuje následující obsah:

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

## <a name="dockerfile"></a>Souboru Dockerfile

V pracovním adresáři vytvořte "souboru Dockerfile" s následujícím obsahem:

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
   > Visual Studio 2017 verze 15,8 nebo starší (jakýkoli produkt) nebude správně nainstalován na MCR\.Microsoft\.com\/Windows\/ServerCore: 1809 nebo novější. Nezobrazuje se žádná chyba.
   >
   > Další informace najdete v tématu [známé problémy pro kontejnery](build-tools-container-issues.md) .

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

Spuštěním následujícího příkazu Sestavte image v aktuálním pracovním adresáři:

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

Volitelně předejte buď `FROM_IMAGE`, nebo `CHANNEL_URL` argumenty pomocí přepínače příkazového řádku `--build-arg`, abyste určili jiný základní obrázek nebo umístění interního rozložení, aby se zachoval pevný obrázek.

## <a name="diagnosing-install-failures"></a>Diagnostikování selhání instalace

Tento příklad stáhne konkrétní nástroje a ověří, že se hodnoty hash shodují. Stáhne také nejnovější nástroj pro shromažďování protokolů sady Visual Studio a .NET, takže pokud dojde k selhání instalace, můžete tyto protokoly zkopírovat do hostitelského počítače a analyzovat tak selhání.

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

Po dokončení provádění posledního řádku otevřete na svém počítači "%TEMP%\vslogs.zip" nebo odešlete problém na webu [komunity vývojářů](https://developercommunity.visualstudio.com) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace Build Tools do kontejneru](build-tools-container.md)
* [Známé problémy s kontejnery](build-tools-container-issues.md)
* [Visual Studio Build Tools úlohy a ID komponent](workload-component-id-vs-build-tools.md)
