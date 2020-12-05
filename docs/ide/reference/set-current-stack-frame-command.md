---
title: Nastavit aktuální rámec zásobníku – příkaz
description: Přečtěte si o příkazu nastavit aktuální rámec zásobníku a o tom, jak vám umožní nastavit konkrétní rámec zásobníku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 032602744247ded5cb38d8a3ae3e1157ccbc5cee
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616600"
---
# <a name="set-current-stack-frame-command"></a>Nastavit aktuální rámec zásobníku – příkaz
Umožňuje nastavit konkrétní rámec zásobníku.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumenty
`index`

Povinná hodnota. Vybere rámec zásobníku podle jeho indexu.

## <a name="example"></a>Příklad

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)