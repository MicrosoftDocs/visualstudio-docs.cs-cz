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
ms.openlocfilehash: abd8ba039f9f6a19f5c028e05c03151c090e304c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631000"
---
# <a name="whats-new-in-msbuild-160"></a>Co je nového v MSBuild 16,0

Tento článek popisuje aktualizované funkce a vlastnosti v MSBuild 16,0. Podrobné poznámky k verzi najdete v tématu [MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Změněná cesta

 Nástroj MSBuild je nainstalován ve složce *\ aktuální* v každé verzi sady Visual Studio. Například *C:\Program Files (x86) \Microsoft Visual Studio\Current\Enterprise\MSBuild*. K vyhledání MSBuild: [vssetup. PowerShellu](https://github.com/Microsoft/vssetup.powershell)můžete použít taky následující modul PowerShellu.

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti nástroje MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion` pro tuto verzi nástrojů je "aktuální". Verze sestavení je stejná jako v aplikaci Visual Studio 2017, která je 15.1.0.0.

- `VisualStudioVersion` pro tuto verzi nástrojů je "16,0"

## <a name="updates"></a>Aktualizace

MSBuild (a Visual Studio) nyní cílí na .NET Framework 4.7.2. Pokud chcete používat nové funkce rozhraní API nástroje MSBuild, musíte upgradovat také sestavení, ale stávající kód bude fungovat i nadále.

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
