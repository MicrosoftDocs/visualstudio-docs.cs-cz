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
ms.openlocfilehash: e2e9177ee7048f626c61fee087468f991e4ed548
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610736"
---
# <a name="list-disassembly-command"></a>Zobrazit zpětný překlad – příkaz
Zahájí proces ladění a umožňuje určit, jak se mají chyby zpracovávat.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Přepínače
Každý přepínač lze vyvolat buď pomocí jeho úplného formátu, nebo krátkého tvaru.

/Count: `number` [nebo]/c: `number` [nebo]/length: `number` [nebo]/l: `number`

Volitelné. Počet instrukcí, které se mají zobrazit Výchozí hodnota je 8.

/endaddress: `expression` [nebo]/e: `expression`

Volitelné. Adresa, na které se má zastavit zpětný překlad.

/codebytes: `yes`&#124; `no` [nebo]/bytes: `yes`&#124; `no` [nebo]/b: `yes`&#124; `no`

Volitelné. Označuje, zda se mají zobrazovat bajty kódu. Výchozí hodnota je `no`.

/Source: `yes`&#124; `no` [nebo]/s: `yes`&#124; `no`

Volitelné. Označuje, zda se má zobrazit zdrojový kód. Výchozí hodnota je `no`.

/symbolnames: `yes`&#124; `no` [nebo]/names: `yes`&#124; `no` [nebo]/n: `yes`&#124; `no`

Volitelné. Označuje, zda se mají zobrazovat názvy symbolů. Výchozí hodnota je `yes`.

 [/linenumbers: `yes`&#124; `no`]

Volitelné. Povoluje zobrazení čísel řádků přidružených ke zdrojovému kódu. Přepínač/source musí mít hodnotu `yes`, aby používal přepínač/linenumbers.

## <a name="example"></a>Příklad

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Viz také

- [Příkaz Listovat zásobník volání](../../ide/reference/list-call-stack-command.md)
- [Příkaz Listovat vlákna](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)