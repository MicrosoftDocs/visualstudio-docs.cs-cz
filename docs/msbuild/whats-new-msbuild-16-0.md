---
title: Co&#39;je nového v MSBuild 16,0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: a80489d216c4316fde2579a0a2d7fdb54478abdf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652804"
---
# <a name="whats-new-in-msbuild-160"></a>Co je nového v MSBuild 16,0

Tento článek popisuje aktualizované funkce a vlastnosti v MSBuild 16,0. Podrobné poznámky k verzi najdete v tématu [MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Změněná cesta

 Nástroj MSBuild je nainstalován ve složce *\ aktuální* v každé verzi sady Visual Studio a spustitelné soubory jsou umístěny v podsložce *\Bin* . Například cesta k nástroji *MSBuild. exe* , která je nainstalovaná se sadou Visual Studio 2019, je *C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* . k nalezení MSBuild: [vssetup. PowerShellu](https://github.com/Microsoft/vssetup.powershell)můžete použít taky následující modul PowerShellu.

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti nástroje MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion` pro tuto verzi nástrojů je "aktuální". Verze sestavení je stejná jako v aplikaci Visual Studio 2017, která je 15.1.0.0.

- `VisualStudioVersion` pro tuto verzi nástrojů je "16,0"

## <a name="updates"></a>Aktualizace

MSBuild (a Visual Studio) nyní cílí na .NET Framework 4.7.2. Pokud chcete používat nové funkce rozhraní API nástroje MSBuild, musíte upgradovat také sestavení, ale stávající kód bude fungovat i nadále.

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
