---
title: -RunExit (devenv. exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 295d4999437248cc9221631378c2beffd80094d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655524"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv. exe)

Zkompiluje a spustí zadaný projekt nebo řešení a potom zavře integrované vývojové prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Úplná cesta a název souboru řešení.

- *Názevprojektu*

  Úplná cesta a název souboru projektu.

- `/Out` *OutputFilename*

  Volitelné. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Zkompiluje a spustí zadaný projekt nebo řešení podle nastavení určeného pro aktivní konfiguraci řešení. Tento přepínač minimalizuje integrované vývojové prostředí (IDE) při spuštění projektu nebo řešení. Ukončí prostředí IDE po dokončení běhu projektu nebo řešení.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace, včetně chyb, se dají zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadaný pomocí přepínače `/Out`.

## <a name="example"></a>Příklad

Tento příklad spustí řešení `MySolution` v minimalizovaném integrovaném vývojovém prostředí pomocí aktivní konfigurace nasazení a pak ukončí rozhraní IDE.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)