---
title: Zobrazit zpětný překlad – příkaz
description: Přečtěte si o příkazu seznam zpětného překladu a o tom, jak zahájí proces ladění, a umožňuje určit, jak se budou zpracovávat chyby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0de7becc46205e5fb8865a0419102bf65afde14e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852086"
---
# <a name="list-disassembly-command"></a>Zobrazit zpětný překlad – příkaz
Zahájí proces ladění a umožňuje určit, jak se mají chyby zpracovávat.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>přepínače,
Každý přepínač lze vyvolat buď pomocí jeho úplného formátu, nebo krátkého tvaru.

/Count: `number` [nebo]/c: `number` [nebo]/length: `number` [nebo]/l: `number`

Nepovinný parametr. Počet instrukcí, které se mají zobrazit Výchozí hodnota je 8.

/endaddress: `expression` [nebo]/e: `expression`

Nepovinný parametr. Adresa, na které se má zastavit zpětný překlad.

/codebytes: `yes`&#124;`no` [nebo]/bytes: `yes`&#124;`no` [nebo]/b: `yes`&#124;`no`

Nepovinný parametr. Označuje, zda se mají zobrazovat bajty kódu. Výchozí hodnota je `no`.

/Source: `yes`&#124;`no` [nebo]/s: `yes`&#124;`no`

Nepovinný parametr. Označuje, zda se má zobrazit zdrojový kód. Výchozí hodnota je `no`.

/symbolnames: `yes`&#124;`no` [nebo]/names: `yes`&#124;`no` [nebo]/n: `yes`&#124;`no`

Nepovinný parametr. Označuje, zda se mají zobrazovat názvy symbolů. Výchozí hodnota je `yes`.

 [/linenumbers: `yes`&#124;`no` ]

Nepovinný parametr. Povoluje zobrazení čísel řádků přidružených ke zdrojovému kódu. Přepínač/source musí mít hodnotu `yes` pro použití přepínače/linenumbers.

## <a name="example"></a>Příklad

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Viz také

- [Listovat zásobník volání – příkaz](../../ide/reference/list-call-stack-command.md)
- [Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)