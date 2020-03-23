---
title: Známé problémy pro kontejnery
description: Další informace o známých problémech, které mohou nastat při instalaci nástrojů pro sestavení sady Visual Studio do kontejneru systému Windows.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a864f1ef623197a44c7d816b051efd0106e86ece
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77611125"
---
# <a name="known-issues-for-containers"></a>Známé problémy pro kontejnery

Existuje několik problémů při instalaci sady Visual Studio do kontejneru Dockeru.

## <a name="windows-container"></a>Kontejner Windows

Následující známé problémy nastanou při instalaci nástroje pro sestavení sady Visual Studio do kontejneru systému Windows.

::: moniker range="vs-2017"

* Sadu Visual Studio nelze nainstalovat do kontejneru založeného na bitové kopii microsoft/windowsservercore:10.0.14393.1593. Obrázky označené verzemi systému Windows před nebo po 10.0.14393 by měly fungovat.

* Sada Windows SDK verze 10.0.14393 nebo starší nelze nainstalovat. Některé balíčky se nezdaří nainstalovat a úlohy, které závisí na těchto balíčků nebude fungovat.

::: moniker-end

* Pass `-m 2GB` (nebo více) při vytváření obrazu. Některé úlohy vyžadují více paměti než výchozí 1 GB při instalaci.
* Nakonfigurujte Docker tak, aby používal disky větší než výchozí 20 GB.
* Předaj `--norestart` příkazový řádek. Od tohoto zápisu se pokus o restartování kontejneru `ERROR_TOO_MANY_OPEN_FILES` systému Windows z kontejneru vrátí hostiteli.
* Pokud bitovou kopii založíte přímo na microsoft/windowsservercore, rozhraní .NET Framework se nemusí správně nainstalovat a není uvedena žádná chyba instalace. Spravovaný kód se nemusí spustit po dokončení instalace. Místo toho založte obrázek na [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Jako příklad se může zobrazit chyba při vytváření s MSBuild, který je podobný následující:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): Chyba MSB6003: Zadaný spustitelný soubor úlohy csc.exe nelze spustit. Nelze načíst soubor nebo sestavení System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a nebo jednu z jeho závislostí. Systém nemůže najít zadaný soubor.

::: moniker range="vs-2017"

* Visual Studio 2017 verze 15.8 nebo starší (jakýkoli produkt) nelze nainstalovat do mcr.microsoft.com/windows/servercore:1809 nebo novější. Další informace naleznete v tématu https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Vytvořit kontejner nástrojů

Při použití kontejneru nástroje sestavení mohou nastat následující známé problémy. Chcete-li zjistit, zda byly problémy opraveny https://developercommunity.visualstudio.comnebo zda existují další známé problémy, navštivte .

* IntelliTrace nemusí fungovat v [některých scénářích](https://github.com/Microsoft/vstest/issues/940) v rámci kontejneru.
* Ve starších verzích Dockeru pro Windows je výchozí velikost image kontejneru pouze 20 GB a nevejde se do nástrojů pro sestavení. Podle [pokynů změňte velikost obrázku](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) na 127 GB nebo více.
Chcete-li potvrdit problém s místem na disku, zkontrolujte další informace v souborech protokolu. Pokud `vslogs\dd_setup_<timestamp>_errors.log` vám dojde místo na disku, bude soubor obsahovat následující: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace Build Tools do kontejneru](build-tools-container.md)
* [Rozšířený příklad pro kontejnery](advanced-build-tools-container.md)
* [Úlohy a ID součástí nástrojů sady Visual Studio](workload-component-id-vs-build-tools.md)
