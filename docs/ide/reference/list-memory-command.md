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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c500b1b516c2b1ab1bc66b7970fccc4ec7a85baa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568708"
---
# <a name="list-memory-command"></a>Listovat paměť – příkaz
Zobrazí obsah zadaného rozsahu paměti.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumenty
`expression`

Nepovinný parametr. Adresa paměti, ze které chcete začít zobrazovat paměť.

## <a name="switches"></a>Přepínače
/ANSI&#124;Unicode

Nepovinný parametr. Zobrazí paměť jako znaky odpovídající bajtům paměti, ansi nebo unicode.

/Počet:`number`

Nepovinný parametr. Určuje, kolik bajtů paměti se má `expression`zobrazit, počínaje .

/Formát:`formattype`

Nepovinný parametr. Typ formátu pro zobrazení informací o paměti v okně **Paměť;** může být OneByte, TwoBytes, FourBytes, EightBytes, Float (32-bit) nebo Double (64bit). Pokud onebyte je `/Unicode` používán, není k dispozici.

/Hex&#124;podepsán&#124;nepodepsaný

Nepovinný parametr. Určuje formát pro zobrazení čísel: jako podepsaný, nepodepsaný nebo šestnáctkový.

## <a name="remarks"></a>Poznámky
Namísto zápisu úplného příkazu **Debug.ListMemory** se všemi přepínači můžete příkaz vyvolat pomocí předdefinovaných aliasů s určitými přepínači přednastavenými na zadané hodnoty. Například místo zadávání:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

můžete napsat:

```cmd
>df /Count:30 /Unicode
```

Zde je seznam dostupných aliasů pro příkaz **Debug.ListMemory:**

|Alias|Příkaz a přepínače|
|-----------| - |
|**D**|Ladění.ListMemory|
|**Da**|Ladění.ListMemory /Ansi|
|**Db**|Ladění.ListMemory /Formát:OneByte|
|**Dc**|Ladění.ListMemory /Formát:FourBytes /Ansi|
|**Dd**|Debug.ListMemory /Format:FourBytes|
|**Df**|Ladění.ListMemory /Formát:Float|
|**Dq**|Debug.ListMemory /Format:Osm bajtů|
|**Du**|Ladění.ListMemory /Unicode|

## <a name="example"></a>Příklad

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Viz také

- [Listovat zásobník volání – příkaz](../../ide/reference/list-call-stack-command.md)
- [Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
