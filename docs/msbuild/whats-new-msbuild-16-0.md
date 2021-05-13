---
title: Co je nového v MSBuild 16,0 | Microsoft Docs
description: Přečtěte si o změněných a aktualizovaných funkcích a vlastnostech pro MSBuild 16,0 a odkaz na poznámky k verzi.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: cdfb552c53a40b6ad2f2349556396475926900be
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848250"
---
# <a name="whats-new-in-msbuild-160"></a>Novinky ve verzi 16.0 nástroje MSBuild

Tento článek popisuje aktualizované funkce a vlastnosti v MSBuild 16,0. Podrobné poznámky k verzi najdete v tématu [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Změněná cesta

 Nástroj MSBuild je nainstalován ve složce *\ aktuální* v každé verzi sady Visual Studio a spustitelné soubory jsou umístěny v podsložce *\Bin* . Například cesta k *MSBuild.exe* nainstalovaná se sadou visual Studio 2019 Community je *C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* můžete také pomocí následujícího modulu PowerShellu najít soubor MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti nástroje MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion` pro tuto verzi nástrojů je to "aktuální". Verze sestavení je stejná jako v aplikaci Visual Studio 2017, která je 15.1.0.0.

- `VisualStudioVersion` pro tuto verzi nástrojů je to "16,0"

## <a name="change-waves"></a>Změna vln

Počínaje nástrojem MSBuild 16,8 můžete selektivně zvolit, zda se chcete odhlásit z určitých potenciálně rušivých změn v nástroji MSBuild. Viz [Změna vlny](change-waves.md).

## <a name="updates"></a>Aktualizace

MSBuild (a Visual Studio) nyní cílí na .NET Framework 4.7.2. Pokud chcete používat nové funkce rozhraní API nástroje MSBuild, musíte upgradovat také sestavení, ale stávající kód bude fungovat i nadále.

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
