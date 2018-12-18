---
title: Nastavit základ – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c18d825ae61dd80ab7b72e1e14c7dc3412582317
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704470"
---
# <a name="set-radix-command"></a>Nastavit základ – příkaz
Nastaví nebo vrátí číselný základní slouží k zobrazení celočíselné hodnoty.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Arguments
 `10` nebo `16` nebo `hex` nebo `dec`

 Volitelné. Určuje desetinné číslo (10 nebo dec) nebo v šestnáctkové soustavě (16 nebo šestnáctkových). Pokud je argument vynechán, je aktuální hodnota základ – vrácena.

## <a name="example"></a>Příklad
 Tento příklad nastaví prostředí k zobrazení hodnot celé číslo v šestnáctkovém formátu.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)