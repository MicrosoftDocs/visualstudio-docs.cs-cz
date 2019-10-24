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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8294c25bcf3b62f9d6480e170d4693a9be85079
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748580"
---
# <a name="toggle-breakpoint-command"></a>Přepnout zarážku – příkaz
Zapne nebo vypne zarážku v závislosti na jejím aktuálním stavu, a to v aktuálním umístění v souboru.

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