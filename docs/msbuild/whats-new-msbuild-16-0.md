---
title: Co&#39;s Novinou v MSBuild 16.0 | Dokumenty společnosti Microsoft
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652804"
---
# <a name="whats-new-in-msbuild-160"></a>Co je nového v msbuild16.0

Tento článek popisuje aktualizované funkce a vlastnosti v msbuild 16.0. Podrobné poznámky k verzi naleznete v [tématu MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Změněná cesta

 MSBuild je nainstalován ve složce *\Current* pod každou verzí sady Visual Studio a spustitelné soubory jsou v podsložce *\Bin.* Například cesta k *nástroji MSBuild.exe* nainstalovanému v komunitě Sady Visual Studio 2019 je *C:\Program Files (x86)\\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* Můžete také vyhledat msbuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)pomocí následujícího modulu PowerShell.

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion`pro tuto verzi nástrojů je "Aktuální". Verze sestavení je stejná jako v sadě Visual Studio 2017, což je 15.1.0.0.

- `VisualStudioVersion`pro tuto verzi nástrojů je "16.0"

## <a name="updates"></a>Aktualizace

MSBuild (a Visual Studio) nyní cílí na .NET Framework 4.7.2. Pokud chcete používat nové funkce rozhraní API nástroje MSBuild, musíte upgradovat také sestavení, ale stávající kód bude fungovat i nadále.

## <a name="see-also"></a>Viz také

- [Msbuild](../msbuild/msbuild.md)
