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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569202"
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
