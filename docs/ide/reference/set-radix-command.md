---
title: Nastavit základ – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e88dc1318e29ddf35073b78218eb113fe8952aac
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769642"
---
# <a name="set-radix-command"></a>Nastavit základ – příkaz
Nastaví nebo vrátí číselnou základnu použitou k zobrazení celočíselných hodnot.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
`10`nebo `16` nebo `hex` or`dec`

Nepovinný parametr. Označuje desetinné číslo (10 nebo DEC) nebo hexadecimální (16 nebo hex). Pokud je argument vynechán, je vrácena aktuální hodnota základu.

## <a name="example"></a>Příklad
Tento příklad nastaví prostředí tak, aby zobrazovalo celočíselné hodnoty v šestnáctkovém formátu.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)