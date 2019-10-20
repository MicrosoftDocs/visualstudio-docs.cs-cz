---
title: Vyhodnotit příkaz příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657712"
---
# <a name="evaluate-statement-command"></a>Ohodnotit příkaz – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyhodnotí a zobrazí daný příkaz.

## <a name="syntax"></a>Syntaxe

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Arguments
 `text` nutné. Příkaz, který se má vyhodnotit

## <a name="remarks"></a>Poznámky
 Okno, které slouží k zadání příkazu **EvaluateStatement** , určuje, zda je znak rovná se (=) interpretován jako operátor porovnání nebo jako operátor přiřazení.

 V **příkazovém** okně je znak rovná se (=) interpretován jako operátor porovnání. Takže pokud se například hodnoty proměnných `a` a `b` liší, pak příkaz

```
>Debug.EvaluateStatement(a=b)
```

 Vrátí hodnotu `false`.

 V **příkazovém podokně** je naopak znak rovná se (=) interpretován jako operátor přiřazení. Například příkaz

```
>Debug.EvaluateStatement(a=b)
```

 se přiřadí proměnné `a` hodnotě proměnné `b`.

## <a name="example"></a>Příklad

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Viz také
 [Print](../../ide/reference/print-command.md) – příkaz příkazy [příkazového řádku](../../ide/reference/command-window.md) [Najít/Command](../../ide/find-command-box.md) v [aplikaci Visual Studio](../../ide/reference/visual-studio-commands.md) – [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
