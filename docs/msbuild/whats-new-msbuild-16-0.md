---
title: Co je &apos; nového v MSBuild 16,0 | Microsoft Docs
description: Přečtěte si o změněných a aktualizovaných funkcích a vlastnostech pro MSBuild 16,0 a odkaz na poznámky k verzi.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: a4e0079fa301d751962a945a0bf8348ffd3c359d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047792"
---
# <a name="whats-new-in-msbuild-160"></a>Novinky ve verzi 16.0 nástroje MSBuild

Tento článek popisuje aktualizované funkce a vlastnosti v MSBuild 16,0. Podrobné poznámky k verzi najdete v tématu [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Změněná cesta

 Nástroj MSBuild je nainstalován ve složce *\ aktuální* v každé verzi sady Visual Studio a spustitelné soubory jsou umístěny v podsložce *\Bin* . Například cesta k *MSBuild.exe* nainstalovaná se sadou visual Studio 2019 Community je *C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* můžete také pomocí následujícího modulu PowerShellu najít soubor MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti nástroje MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion` pro tuto verzi nástrojů je to "aktuální". Verze sestavení je stejná jako v aplikaci Visual Studio 2017, která je 15.1.0.0.

- `VisualStudioVersion` pro tuto verzi nástrojů je to "16,0"

## <a name="updates"></a>Aktualizace

MSBuild (a Visual Studio) nyní cílí na .NET Framework 4.7.2. Pokud chcete používat nové funkce rozhraní API nástroje MSBuild, musíte upgradovat také sestavení, ale stávající kód bude fungovat i nadále.

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
