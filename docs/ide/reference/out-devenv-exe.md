---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a073b4815a01696c546dc2a9dd1132e3605281e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655788"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Určuje soubor pro ukládání a zobrazování chyb při [spuštění](run-devenv-exe.md), [spuštění a ukončení](runexit-devenv-exe.md), [upgrade](upgrade-devenv-exe.md), [sestavení](build-devenv-exe.md), opětovné [sestavení](rebuild-devenv-exe.md), [Vyčištění](clean-devenv-exe.md)nebo [nasazení](deploy-devenv-exe.md) řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Arguments

- *Bitmap*

  Požadováno. Cesta a název souboru, který má dostat výstup při vytváření spustitelného souboru.

## <a name="remarks"></a>Poznámky

Pokud je zadán neexistující název souboru, je soubor vytvořen automaticky. V opačném případě soubor již existuje a výsledky budou připojeny k existujícímu obsahu souboru.

Chyby sestavení příkazového řádku se zobrazí v **příkazovém** okně a v zobrazení tvůrce řešení v okně **výstup** . Tento přepínač je vhodný pro zobrazení výsledků bezobslužných sestavení.

## <a name="example"></a>Příklad

V tomto příkladu se spustí `MySolution` a zapíše chyby do souboru `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv. exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv. exe)](upgrade-devenv-exe.md)
- [/Clean (devenv. exe)](clean-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)