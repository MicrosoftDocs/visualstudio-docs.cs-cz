---
title: Zobrazit zpětný překlad – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaeab2e65088b8f1bfce3a6a12f8cd66c3245b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747926"
---
# <a name="list-disassembly-command"></a>Zobrazit zpětný překlad – příkaz
Zahájí proces ladění a umožňuje určit způsob zpracování chyb.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Přepínače
Každý přepínač lze vyvolat pomocí jeho kompletní formulář nebo krátký formulář.

/count: `number` [or] /c: `number` [or] `number` /length: [or] /l:`number`

Nepovinný parametr. Počet pokynů k zobrazení. Výchozí hodnota je 8.

/koncová `expression` adresa: [nebo] /e:`expression`

Nepovinný parametr. Adresa, na které chcete zastavit demontáž.

/codebytes:`yes` `no`&#124;[nebo] /bytes:`yes`&#124;`no` [or] /b:`yes`&#124;`no`

Nepovinný parametr. Označuje, zda se mají zobrazit bajty kódu. Výchozí hodnota `no`je .

/zdroj:`yes` `no`&#124;[nebo]`yes` /s:&#124;`no`

Nepovinný parametr. Označuje, zda se má zobrazit zdrojový kód. Výchozí hodnota `no`je .

/symbolnames:`yes` `no`&#124;[or]`yes` /names:&#124;`no` [or] /n:`yes`&#124;`no`

Nepovinný parametr. Označuje, zda se mají zobrazovat názvy symbolů. Výchozí hodnota `yes`je .

 [/čísla`yes` řádků: `no`&#124;]

Nepovinný parametr. Umožňuje zobrazení čísel řádků přidružených ke zdrojovému kódu. Přepínač /source musí mít `yes` hodnotu přepínače /linenumbers.

## <a name="example"></a>Příklad

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Viz také

- [Listovat zásobník volání – příkaz](../../ide/reference/list-call-stack-command.md)
- [Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)