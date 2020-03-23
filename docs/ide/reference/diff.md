---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bb74501c15e961d8da8e1e29dd0d9979c79a305
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570086"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Porovná dva soubory. Rozdíly jsou zobrazeny ve speciálním okně sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumenty

- *Zdrojový soubor*

  Povinná hodnota. Úplná cesta a název prvního souboru, který má být porovnán.

- *Cílový soubor*

  Povinná hodnota. Úplná cesta a název druhého souboru, který má být porovnán.

- *Název_sourcedisplayname*

  Nepovinný parametr. Zobrazovaný název prvního souboru.

- *TargetDisplayName*

  Nepovinný parametr. Zobrazovaný název druhého souboru.

## <a name="remarks"></a>Poznámky

Pokud je instance ide je již otevřena, porovnání souborů se zobrazí na kartě v aktuálním ide.

## <a name="example"></a>Příklad

První příklad porovnává dva soubory beze změny jejich zobrazované názvy. Druhý příklad porovnává soubory při změně obou jejich zobrazovaných názvů. Třetí a čtvrtý příklad porovnádva soubory, ale použije alias pouze na první nebo druhý soubor.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
