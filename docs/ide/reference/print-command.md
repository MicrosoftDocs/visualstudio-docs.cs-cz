---
title: Ladit. tisk
description: Přečtěte si o příkazu Print a o tom, jak vyhodnocuje výraz nebo zobrazuje zadaný text.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0524ce015ea4675254615c11e5768e59049c37f6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304132"
---
# <a name="print-command"></a>Tisk – příkaz

Vyhodnotí výraz nebo zobrazí zadaný text.

## <a name="syntax"></a>Syntaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumenty

`text`

Povinná hodnota. Výraz, který se má vyhodnotit, nebo text, který se má zobrazit

## <a name="remarks"></a>Poznámky

Jako alias pro tento příkaz můžete použít otazník (?). Například příkaz

```cmd
>Debug.Print expA
```

lze také zapsat jako

```cmd
? expA
```

Obě verze tohoto příkazu vracejí aktuální hodnotu výrazu `expA` .

## <a name="example"></a>Příklad

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Viz také

- [Evaluate – příkaz příkazu](../../ide/reference/evaluate-statement-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
