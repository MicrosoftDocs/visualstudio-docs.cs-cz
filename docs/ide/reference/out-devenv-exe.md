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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568008"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Určuje soubor, který má být při [spuštění](run-devenv-exe.md)ukládán a zobrazuje chyby , [spouštějí a ukončují](runexit-devenv-exe.md), [inovují](upgrade-devenv-exe.md), [vytvářejí](build-devenv-exe.md), [ukončují](clean-devenv-exe.md)nebo [nasazují](deploy-devenv-exe.md) řešení. [rebuild](rebuild-devenv-exe.md)

## <a name="syntax"></a>Syntaxe

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumenty

- *Název_souboru*

  Povinná hodnota. Cesta a název souboru pro příjem výstupu při vytváření spustitelného souboru.

## <a name="remarks"></a>Poznámky

Pokud je zadán neexistující název souboru, soubor se vytvoří automaticky. V opačném případě soubor již existuje a výsledky jsou připojeny k existujícímu obsahu souboru.

Chyby sestavení příkazového řádku se zobrazují v okně **Příkaz** a v zobrazení Tvůrce řešení v okně **Výstup.** Tento přepínač je užitečný pro zobrazení výsledků bezobslužných sestavení.

## <a name="example"></a>Příklad

Tento příklad `MySolution` spustí a zapíše chyby do souboru `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Znovu sestavit (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
