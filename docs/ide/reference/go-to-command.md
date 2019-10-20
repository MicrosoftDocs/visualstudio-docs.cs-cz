---
title: Přejít na – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93ad14561b1fdd2aade1978831b784e014568a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668253"
---
# <a name="go-to-command"></a>Přejít na – příkaz
Přesune kurzor na zadaný řádek.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
`linenumber`\
Volitelné. Celé číslo představující číslo řádku, na který se má přejít

## <a name="remarks"></a>Poznámky
Číslování řádků začíná na jednom. Pokud je hodnota `linenumber` menší než jedna, zobrazí se první řádek. Pokud je hodnota `linenumber` větší než číslo posledního řádku, zobrazí se poslední řádek.

Pokud není zadána hodnota `linenumber`, zobrazí se dialogové okno **Přejít na řádek** .

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