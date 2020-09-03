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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cda81d37be0246c1181b4d82cbd17c3119b94437
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568008"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Určuje soubor pro ukládání a zobrazování chyb při [spuštění](run-devenv-exe.md), [spuštění a ukončení](runexit-devenv-exe.md), [upgrade](upgrade-devenv-exe.md), [sestavení](build-devenv-exe.md), opětovné [sestavení](rebuild-devenv-exe.md), [Vyčištění](clean-devenv-exe.md)nebo [nasazení](deploy-devenv-exe.md) řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumenty

- *Bitmap*

  Povinná hodnota. Cesta a název souboru, který má dostat výstup při vytváření spustitelného souboru.

## <a name="remarks"></a>Poznámky

Pokud je zadán neexistující název souboru, je soubor vytvořen automaticky. V opačném případě soubor již existuje a výsledky budou připojeny k existujícímu obsahu souboru.

Chyby sestavení příkazového řádku se zobrazí v **příkazovém** okně a v zobrazení tvůrce řešení v okně **výstup** . Tento přepínač je vhodný pro zobrazení výsledků bezobslužných sestavení.

## <a name="example"></a>Příklad

Tento příklad `MySolution` se spustí a zapíše chyby do souboru `MyErrorLog.txt` .

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
