---
title: Nastavit základ příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665422"
---
# <a name="set-radix-command"></a>Nastavit základ – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví nebo vrátí číselnou základnu použitou k zobrazení celočíselných hodnot.

## <a name="syntax"></a>Syntaxe

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
 `10` nebo `16` nebo `hex` `dec` volitelné. Označuje desetinné číslo (10 nebo DEC) nebo hexadecimální (16 nebo hex). Pokud je argument vynechán, je vrácena aktuální hodnota základu.

## <a name="example"></a>Příklad
 Tento příklad nastaví prostředí tak, aby zobrazovalo celočíselné hodnoty v šestnáctkovém formátu.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
