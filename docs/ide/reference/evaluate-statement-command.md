---
title: Ohodnotit příkaz – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f713cd511225e03ec50c2cbe699c40bd704faa20
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704233"
---
# <a name="evaluate-statement-command"></a>Ohodnotit příkaz – příkaz
Vyhodnotí a zobrazí daný příkaz.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Arguments
 `text` Vyžaduje se. Příkaz k vyhodnocení.

## <a name="remarks"></a>Poznámky
 Okno používané k zadání **EvaluateStatement** příkaz určuje, zda znak rovná se (=) interpretována jako relační operátor nebo operátor přiřazení.

 V **příkaz** okně znak rovná se (=) interpretována jako operátor porovnání. Ano, například pokud hodnoty proměnných `a` a `b` jsou různé a potom příkaz

```cmd
>Debug.EvaluateStatement(a=b)
```

 Vrátí hodnotu `false`.

 V **Immediate** okně naopak znak rovná se (=) interpretována jako operátor přiřazení. Tak například příkaz

```cmd
>Debug.EvaluateStatement(a=b)
```

 přiřadí do proměnné `a` hodnotu proměnné `b`.

## <a name="example"></a>Příklad

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Viz také

- [Příkaz Tisk](../../ide/reference/print-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)