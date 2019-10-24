---
title: -Run (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 051462339ea25dde9c2b55394e1854c60a71dc7e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747764"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Zkompiluje a spustí zadaný projekt nebo řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Úplná cesta a název souboru řešení.

- *Názevprojektu*

  Úplná cesta a název souboru projektu.

- `/Out` *OutputFilename*

  Volitelné. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Zkompiluje a spustí zadaný projekt nebo řešení podle nastavení určeného pro aktivní konfiguraci řešení. Tento přepínač spustí rozhraní IDE a nechá ho aktivní po dokončení běhu projektu nebo řešení.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace, včetně chyb, se dají zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadaný pomocí přepínače `/Out`.

## <a name="example"></a>Příklad

Tento příklad spustí řešení `MySolution` pomocí aktivní konfigurace nasazení.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv. exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)