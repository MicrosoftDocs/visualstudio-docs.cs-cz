---
title: Přejít na – příkaz
description: Přečtěte si o příkazu Přejít na a o tom, jak přesune kurzor na určený řádek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305210"
---
# <a name="go-to-command"></a>Přejít na – příkaz
Přesune kurzor na zadaný řádek.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumenty
`linenumber`\
Nepovinný parametr. Celé číslo představující číslo řádku, na který se má přejít

## <a name="remarks"></a>Poznámky
Číslování řádků začíná na jednom. Pokud hodnota `linenumber` je menší než jedna, zobrazí se první řádek. Pokud `linenumber` je hodnota větší než číslo posledního řádku, zobrazí se poslední řádek.

Pokud není zadána hodnota pro `linenumber` , zobrazí se dialogové okno **Přejít na řádek** .

Alias pro tento příkaz je GoToLn.

## <a name="example"></a>Příklad

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
