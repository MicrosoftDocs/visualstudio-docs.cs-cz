---
title: Zobrazit zpětný překlad – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64951810020d99239a47b9c6bdba751b2c0a3dfd
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704730"
---
# <a name="list-disassembly-command"></a>Zobrazit zpětný překlad – příkaz
Zahájí proces ladění a umožňuje vám určit způsob zpracování chyb.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Přepínače
 Každý přepínač lze vyvolat pomocí jeho dokončení formuláře nebo zkrácené formě.

 / count: `number` [nebo] / c: `number` [nebo] /length: `number` [nebo] l: `number`

 Volitelné. Počet pokyny pro zobrazení. Výchozí hodnota je 8.

 /endaddress: `expression` [nebo] / e: `expression`

 Volitelné. Adresa, kam chcete zastavit zpětný překlad.

 /codebytes:`yes` &#124; `no` [nebo] /bytes:`yes` &#124; `no` [nebo] / b:`yes`&#124;`no`

 Volitelné. Označuje, zda se mají zobrazovat kód bajty. Výchozí hodnota je `no`.

 / source:`yes` &#124; `no` [nebo] / s:`yes`&#124;`no`

 Volitelné. Určuje, jestli se má zobrazit zdrojový kód. Výchozí hodnota je `no`.

 /symbolnames:`yes` &#124; `no` [nebo] /names:`yes` &#124; `no` [nebo] / n:`yes`&#124;`no`

 Volitelné. Označuje, zda chcete zobrazit názvy symbolů. Výchozí hodnota je `yes`.

 [/ linenumbers:`yes`&#124;`no`]

 Volitelné. Povolí zobrazování čísla řádků související se zdrojovým kódem. Přepínač/Source musí mít hodnotu `yes` na používání /linenumbers přepínače.

## <a name="example"></a>Příklad

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Viz také

- [Příkaz Listovat zásobník volání](../../ide/reference/list-call-stack-command.md)
- [Příkaz Listovat vlákna](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)