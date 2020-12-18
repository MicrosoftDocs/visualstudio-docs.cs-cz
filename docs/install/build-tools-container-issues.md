---
title: Známé problémy pro kontejnery
description: Další informace o známých problémech, ke kterým může dojít při instalaci Visual Studio Build Tools do kontejneru Windows.
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
ms.openlocfilehash: cf8473a8de1c9afa5ed73ce9dcb6b9b8462e6548
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668392"
---
# <a name="known-issues-for-containers"></a>Známé problémy pro kontejnery

Při instalaci sady Visual Studio do kontejneru Docker je k dispozici několik problémů.

## <a name="windows-container"></a>Kontejner Windows

Při instalaci Visual Studio Build Tools do kontejneru Windows dochází k následujícím známým problémům.

::: moniker range="vs-2017"

* Nejde nainstalovat Visual Studio do kontejneru založeného na Image Microsoft/windowsservercore: 10.0.14393.1593. Obrázky označené verzemi Windows před nebo po 10.0.14393 by měly fungovat.

* Nemůžete nainstalovat Windows SDK verze 10.0.14393 nebo starší. Některé balíčky se nedaří nainstalovat a úlohy, které na těchto balíčcích závisejí, nebudou fungovat.

::: moniker-end

* Předat `-m 2GB` (nebo další) při sestavování obrázku. Některé úlohy vyžadují při instalaci více paměti, než je výchozí 1 GB.
* Nakonfigurujte Docker tak, aby používal disky větší než výchozí 20 GB.
* Předat `--norestart` na příkazovém řádku. V rámci tohoto psaní se při pokusu o restartování kontejneru Windows z kontejneru vrátí `ERROR_TOO_MANY_OPEN_FILES` do hostitele.
* Pokud bitovou kopii založíte přímo na Microsoft/windowsservercore, .NET Framework se nemusí správně nainstalovat a nebude se naznačit žádná chyba instalace. Spravovaný kód se po dokončení instalace nemusí spustit. Místo toho použijte obrázek na bázi [Microsoft/DotNET-Framework: 4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) nebo novější. Jako příklad se může zobrazit chyba při sestavování s nástrojem MSBuild, který je podobný následujícímu:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets (84, 5): Chyba MSB6003: nelze spustit zadaný spustitelný soubor úlohy csc.exe. Nelze načíst soubor nebo sestavení System. IO. FileSystem, verze = 4.0.1.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' nebo jedna z jeho závislostí. Systém nemůže najít zadaný soubor.

::: moniker range="vs-2017"

* Nemůžete nainstalovat Visual Studio 2017 verze 15,8 nebo starší (jakýkoli produkt) na mcr.microsoft.com/windows/servercore:1809 nebo novějším. Další informace naleznete v tématu https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Kontejner nástrojů sestavení

Při použití kontejneru nástrojů sestavení mohou nastat následující známé problémy. Pokud chcete zjistit, jestli byly problémy vyřešené nebo jestli existují další známé problémy, navštivte [komunitu vývojářů](https://aka.ms/feedback/suggest?space=8).

* IntelliTrace nemusí fungovat v [některých scénářích](https://github.com/Microsoft/vstest/issues/940) v rámci kontejneru.
* Ve starších verzích Docker for Windows je výchozí velikost kontejneru kontejneru pouze 20 GB a nebude odpovídat nástrojům sestavení. Podle [pokynů změňte velikost obrázku](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) na 127 GB nebo více.
Pokud chcete potvrdit problém místo na disku, vyhledejte další informace v souborech protokolu. `vslogs\dd_setup_<timestamp>_errors.log`Pokud vyčerpáte místo na disku, bude soubor obsahovat následující: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace Build Tools do kontejneru](build-tools-container.md)
* [Rozšířený příklad pro kontejnery](advanced-build-tools-container.md)
* [Visual Studio Build Tools úlohy a ID komponent](workload-component-id-vs-build-tools.md)
