---
title: Debug.Print –
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
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567837"
---
# <a name="print-command"></a>Tisk – příkaz

Vyhodnotí výraz nebo zobrazí zadaný text.

## <a name="syntax"></a>Syntaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Arguments

`text`

Požadováno. Výraz, který se má vyhodnotit, nebo text, který se má zobrazit

## <a name="remarks"></a>Poznámky

Jako alias pro tento příkaz můžete použít otazník (?). Například příkaz

```cmd
>Debug.Print expA
```

lze také zapsat jako

```cmd
? expA
```

Obě verze tohoto příkazu vrátí aktuální hodnotu výrazu `expA`.

## <a name="example"></a>Příklad

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Viz také:

- [Příkaz Ohodnotit příkaz](../../ide/reference/evaluate-statement-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
