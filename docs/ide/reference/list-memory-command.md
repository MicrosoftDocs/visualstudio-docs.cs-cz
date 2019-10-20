---
title: Listovat paměť – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb5e6181c2dbe9a79b2ab1d0859722de324d768e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610699"
---
# <a name="list-memory-command"></a>Listovat paměť – příkaz
Zobrazí obsah zadaného rozsahu paměti.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
`expression`

Volitelné. Adresa paměti, ze které se má začít zobrazovat paměť

## <a name="switches"></a>Přepínače
/ANSI&#124;Unicode

Volitelné. Zobrazí paměť jako znaky odpovídající bajtům paměti, a to buď ANSI nebo Unicode.

/Count: `number`

Volitelné. Určuje, kolik bajtů paměti se má zobrazit, počínaje `expression`.

/Format: `formattype`

Volitelné. Typ formátu pro zobrazení informací o paměti v okně **paměti** ; může být OneByte, TwoBytes, FourBytes, EightBytes, float (32-bit) nebo Double (64-bit). Pokud se používá OneByte, `/Unicode` není k dispozici.

/Hex&#124;podepsané&#124;bez znaménka

Volitelné. Určuje formát pro zobrazení čísel: jako podepsaný, unsigned nebo hexadecimální.

## <a name="remarks"></a>Poznámky
Místo zapsání kompletního příkazu **Debug. ListMemory –** se všemi přepínači můžete vyvolat příkaz pomocí předdefinovaných aliasů s určitými přepínači předem zadaným hodnotám. Například namísto zadání:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

můžete napsat:

```cmd
>df /Count:30 /Unicode
```

Tady je seznam dostupných aliasů pro příkaz **Debug. ListMemory –** :

|Alias|Příkazy a přepínače|
|-----------| - |
|**trojrozměrné**|Debug. ListMemory –|
|**&**|Ladit. ListMemory –/ANSI|
|**inženýr**|Debug. ListMemory –/Format: OneByte|
|**DC**|Debug. ListMemory –/Format: FourBytes/ANSI|
|**DD**|Debug. ListMemory –/Format: FourBytes|
|**příznak**|Debug. ListMemory –/Format: float|
|**DQ**|Debug. ListMemory –/Format: EightBytes|
|**du**|Ladit. ListMemory –/Unicode|

## <a name="example"></a>Příklad

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Viz také

- [Příkaz Listovat zásobník volání](../../ide/reference/list-call-stack-command.md)
- [Příkaz Listovat vlákna](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)