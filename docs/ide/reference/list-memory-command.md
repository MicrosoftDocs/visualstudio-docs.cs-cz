---
title: Listovat paměť – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57d6c8c7821df8bd22723900ebd011c110a1857f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815179"
---
# <a name="list-memory-command"></a>Listovat paměť – příkaz
Zobrazí obsah určeného rozsahu paměti.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
 `expression`

 Volitelné. Adresa paměti, ze kterého se má zahájit zobrazování paměti.

## <a name="switches"></a>Přepínače
 / ANSI&#124;kódování Unicode

 Volitelné. Zobrazení paměti jako odpovídající počet bajtů paměti, ANSI nebo Unicode znaky.

 / Počet:`number`

 Volitelné. Určuje počet bajtů paměti k zobrazení, počínaje `expression`.

 / Formát:`formattype`

 Volitelné. Formát typu pro zobrazení informací o paměti v **paměti** okno; je pravděpodobně být OneByte TwoBytes, FourBytes, EightBytes, Float (32bitová verze) nebo dvakrát (64 bitů). Pokud použijete OneByte `/Unicode` není k dispozici.

 / Hex&#124;podepsané&#124;bez znaménka

 Volitelné. Určuje formát zobrazení čísel: jako podepsaný držitelem, bez znaménka nebo šestnáctkové.

## <a name="remarks"></a>Poznámky
 Místo psaní si kompletní **Debug.listmemory –** příkazu se všechny přepínače, můžete vyvolat příkaz předdefinované aliasy using s určitým přepínači přednastaveny tak, aby zadané hodnoty. Například místo zadávání:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 můžete psát:

```cmd
>df /Count:30 /Unicode
```

 Tady je seznam dostupné aliasy pro **Debug.listmemory –** příkaz:

|Alias|Příkaz a přepínače|
|-----------| - |
|**d**|Debug.listmemory –|
|**da**|Debug.listmemory – /Ansi|
|**DB**|Debug.listmemory – /Format:OneByte|
|**řadič domény**|Debug.listmemory – /Format:FourBytes /Ansi|
|**dd**|Debug.listmemory – /Format:FourBytes|
|**DF**|Debug.listmemory – /Format:Float|
|**dq**|Debug.listmemory – /Format:EightBytes|
|**rozlišované sjednocení typu**|Debug.listmemory – Unicode|

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