---
title: -Diff (devenv.exe)
description: Přečtěte si, jak použít rozdílový přepínač příkazového řádku devenv k porovnání dvou souborů.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a8c4c8868de187b9e9aa5183e44c29145220e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882144"
---
# <a name="diff-devenvexe"></a>Diff (devenv.exe)

Porovná dva soubory. Rozdíly se zobrazí ve speciálním okně sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumenty

- *Požadovaný sourcefile*

  Povinná hodnota. Úplná cesta a název prvního souboru, který se má porovnat

- *CílovýSoubor*

  Povinná hodnota. Úplná cesta a název druhého souboru, který se má porovnat

- *Zdrojovýnázevzobrazení*

  Nepovinný parametr. Zobrazovaný název prvního souboru.

- *Cílovýnázevzobrazení*

  Nepovinný parametr. Zobrazovaný název druhého souboru

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

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
