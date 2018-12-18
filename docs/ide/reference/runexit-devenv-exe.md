---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dff2f028c94013df4f69e9aca244f98c307d2782
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948228"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Zkompiluje a spustí zadaný projekt nebo řešení a potom jej zavře integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments
 `SolutionName`

 Požadováno. Úplná cesta a název souboru řešení.

 `ProjectName`

 Požadováno. Úplná cesta a název souboru projektu.

## <a name="remarks"></a>Poznámky
 Zkompiluje a spustí zadaný projekt nebo řešení podle nastavení nakonfigurovaného pro konfiguraci aktivního řešení. Tento přepínač minimalizuje rozhraní IDE při projekt nebo řešení je spustit a ho ukončí rozhraní IDE po projekt nebo řešení po dokončení jeho běhu.

-   Uzavření řetězců, které obsahují mezery v dvojitých uvozovkách.

-   Souhrnné informace, včetně chyb, lze zobrazit v **příkaz** okna, nebo do jakéhokoli souboru protokolu zadaný `/out` přepnout.

## <a name="example"></a>Příklad
 Tento příklad spustí řešení `MySolution` v minimalizovaném okně integrovaného vývojového prostředí pomocí konfigurace aktivního nasazení a poté ukončí rozhraní IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [Nebo spuštění (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)