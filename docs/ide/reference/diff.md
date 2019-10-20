---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d438e9cea35cbf178658d8def78e264804240c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654515"
---
# <a name="diff-devenvexe"></a>Diff (devenv. exe)

Porovná dva soubory. Rozdíly se zobrazí ve speciálním okně sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Arguments

- *Požadovaný sourcefile*

  Požadováno. Úplná cesta a název prvního souboru, který se má porovnat

- *CílovýSoubor*

  Požadováno. Úplná cesta a název druhého souboru, který se má porovnat

- *Zdrojovýnázevzobrazení*

  Volitelné. Zobrazovaný název prvního souboru.

- *Cílovýnázevzobrazení*

  Volitelné. Zobrazovaný název druhého souboru

## <a name="remarks"></a>Poznámky

Je-li již instance rozhraní IDE otevřena, porovnání souborů se zobrazí na kartě v aktuálním integrovaném vývojovém prostředí (IDE).

## <a name="example"></a>Příklad

První příklad Porovná dva soubory beze změny zobrazovaných názvů. Druhý příklad porovná soubory a zároveň změní oba zobrazované názvy. Třetí a čtvrtý příklad porovnávají dva soubory, ale alias aplikujte pouze na první soubor nebo druhý soubor.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
