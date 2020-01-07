---
title: Přepnout zarážku – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d393890e6166b4a4ef53c9520a556e9a9edd64d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597318"
---
# <a name="toggle-breakpoint-command"></a>Přepnout zarážku – příkaz
V závislosti na jejím aktuálním stavu na aktuální pozici v souboru se změní na zarážku, zapnout nebo vypnout.

## <a name="syntax"></a>Syntaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Arguments

`text`\
Volitelné. Je-li zadán text, je řádek označen jako pojmenovaná zarážka. V opačném případě je řádek označený jako Nepojmenovaná zarážka, což se podobá tomu, co se stane po stisknutí klávesy F9.

## <a name="example"></a>Příklad
Následující příklad přepíná aktuální zarážku.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
