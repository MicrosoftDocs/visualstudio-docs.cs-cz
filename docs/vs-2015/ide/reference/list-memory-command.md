---
title: Výpis paměti – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672749"
---
# <a name="list-memory-command"></a>Listovat paměť – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazí obsah zadaného rozsahu paměti.

## <a name="syntax"></a>Syntaxe

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumenty
 `expression` Volitelné. Adresa paměti, ze které se má začít zobrazovat paměť

## <a name="switches"></a>Přepínače
 /ANSI&#124;kódování Unicode volitelné. Zobrazí paměť jako znaky odpovídající bajtům paměti, a to buď ANSI nebo Unicode.

 /Count: `number` volitelné. Určuje, kolik bajtů paměti se má zobrazit, od `expression` .

 /Format: `formattype` volitelné. Typ formátu pro zobrazení informací o paměti v okně **paměti** ; může být OneByte, TwoBytes, FourBytes, EightBytes, float (32-bit) nebo Double (64-bit). Pokud se používá OneByte, `/Unicode` není k dispozici.

 /Hex&#124;podepsané&#124;bez znaménka není povinné. Určuje formát pro zobrazení čísel: jako podepsaný, unsigned nebo hexadecimální.

## <a name="remarks"></a>Poznámky
 Místo zapsání kompletního příkazu **Debug. ListMemory –** se všemi přepínači můžete vyvolat příkaz pomocí předdefinovaných aliasů s určitými přepínači předem zadaným hodnotám. Například namísto zadání:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 můžete napsat:

```
>df /Count:30 /Unicode
```

 Tady je seznam dostupných aliasů pro příkaz **Debug. ListMemory –** :

|Alias|Příkazy a přepínače|
|-----------|--------------------------|
|**trojrozměrné**|Debug. ListMemory –|
|**&**|Ladit. ListMemory –/ANSI|
|**inženýr**|Debug. ListMemory –/Format: OneByte|
|**DC**|Debug. ListMemory –/Format: FourBytes/ANSI|
|**DD**|Debug. ListMemory –/Format: FourBytes|
|**příznak**|Debug. ListMemory –/Format: float|
|**DQ**|Debug. ListMemory –/Format: EightBytes|
|**du**|Ladit. ListMemory –/Unicode|

## <a name="example"></a>Příklad

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Viz také
 Vypsat seznam příkazů výpisu [zásobníku volání](../../ide/reference/list-call-stack-command.md) [příkaz](../../ide/reference/list-threads-command.md) [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md) [příkaz](../../ide/reference/command-window.md) [Najít/příkazové](../../ide/find-command-box.md) okno [Visual Studio aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md)
