---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18ca581c5a8a7f631138e8b3eacff02a031e0931
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593600"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Zkompiluje a spustí zadaný projekt nebo řešení a potom zavře integrované vývojové prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Úplná cesta a název souboru řešení.

- *Projectname*

  Úplná cesta a název souboru projektu.

- `/Out`*Název_výstupního souboru*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Zkompiluje a spustí zadaný projekt nebo řešení podle nastavení určeného pro konfiguraci aktivního řešení. Tento přepínač minimalizuje ide při spuštění projektu nebo řešení. Zavře ide po dokončení projektu nebo řešení.

- Uzavřete řetězce, které obsahují mezery v uvozovkách.

- Souhrnné informace, včetně chyb, lze zobrazit v okně **Příkaz** nebo v `/Out` libovolném souboru protokolu určeném přepínačem.

## <a name="example"></a>Příklad

Tento příklad spustí `MySolution` řešení v minimalizovaném ide pomocí konfigurace aktivní nasazení a potom zavře ide.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Znovu sestavit (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
