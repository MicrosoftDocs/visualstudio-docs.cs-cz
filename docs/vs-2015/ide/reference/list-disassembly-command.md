---
title: Výpis zpětného překladu příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672744"
---
# <a name="list-disassembly-command"></a>Zobrazit zpětný překlad – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zahájí proces ladění a umožňuje určit, jak se mají chyby zpracovávat.

## <a name="syntax"></a>Syntaxe

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Přepínače
 Každý přepínač lze vyvolat buď pomocí jeho úplného formátu, nebo krátkého tvaru.

 /Count: `number` [nebo]/c: `number` [or]/length: `number` [nebo]/l: `number` volitelné. Počet instrukcí, které se mají zobrazit Výchozí hodnota je 8.

 /endaddress: `expression` [nebo]/e: `expression` volitelné. Adresa, na které se má zastavit zpětný překlad.

 /codebytes: `yes`&#124; `no` [nebo]/bytes: `yes`&#124; `no` [nebo]/B: `yes`&#124; `no` volitelné. Označuje, zda se mají zobrazovat bajty kódu. Výchozí hodnota je `no`.

 /Source: `yes`&#124; `no` [nebo]/s: `yes`&#124; `no` volitelné. Označuje, zda se má zobrazit zdrojový kód. Výchozí hodnota je `no`.

 /symbolnames: `yes`&#124; `no` [nebo]/names: `yes`&#124; `no` [nebo]/N: `yes`&#124; `no` volitelné. Označuje, zda se mají zobrazovat názvy symbolů. Výchozí hodnota je `yes`.

 [/linenumbers: `yes`&#124; `no`] Volitelné. Povoluje zobrazení čísel řádků přidružených ke zdrojovému kódu. Přepínač/source musí mít hodnotu `yes`, aby používal přepínač/linenumbers.

## <a name="example"></a>Příklad

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Viz také
 Vypsat seznam příkazů výpisu [zásobníku volání](../../ide/reference/list-call-stack-command.md) [příkaz](../../ide/reference/list-threads-command.md) [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md) [příkaz](../../ide/reference/command-window.md) [Najít/příkazové](../../ide/find-command-box.md) okno [Visual Studio aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md)
