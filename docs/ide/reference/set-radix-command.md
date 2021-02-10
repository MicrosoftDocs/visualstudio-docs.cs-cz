---
title: Nastavit základ – příkaz
description: Přečtěte si o příkazu set základ a o tom, jak nastaví nebo vrátí číselnou základnu použitou k zobrazení celočíselných hodnot.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50d0097debbd7e91906202b85e8e9e6dab36a27d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957683"
---
# <a name="set-radix-command"></a>Nastavit základ – příkaz
Nastaví nebo vrátí číselnou základnu použitou k zobrazení celočíselných hodnot.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
`10` nebo `16` nebo `hex` or `dec`

Nepovinný parametr. Označuje desetinné číslo (10 nebo DEC) nebo hexadecimální (16 nebo hex). Pokud je argument vynechán, je vrácena aktuální hodnota základu.

## <a name="example"></a>Příklad
Tento příklad nastaví prostředí tak, aby zobrazovalo celočíselné hodnoty v šestnáctkovém formátu.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)