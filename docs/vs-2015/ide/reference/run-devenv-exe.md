---
title: -Run (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665527"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zkompiluje a spustí zadaný projekt nebo řešení.

## <a name="syntax"></a>Syntaxe

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments
 `SolutionName` nutné. Úplná cesta a název souboru řešení.

 `ProjectName` nutné. Úplná cesta a název souboru projektu.

## <a name="remarks"></a>Poznámky
 Zkompiluje a spustí zadaný projekt nebo řešení podle nastavení určeného pro aktivní konfiguraci řešení. Tento přepínač spustí integrované vývojové prostředí (IDE) a po dokončení projektu nebo řešení ho opustí aktivní.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace, včetně chyb, se dají zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadaný pomocí přepínače `/out`.

## <a name="example"></a>Příklad
 Tento příklad spustí řešení `MySolution` pomocí aktivní konfigurace nasazení.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md) [/Runexit (devenv. exe)](../../ide/reference/runexit-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
