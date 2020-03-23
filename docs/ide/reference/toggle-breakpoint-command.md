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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597318"
---
# <a name="toggle-breakpoint-command"></a>Přepnout zarážku – příkaz
Zapne nebo vypne zarážku v závislosti na aktuálním stavu v aktuálním umístění v souboru.

## <a name="syntax"></a>Syntaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumenty

`text`\
Nepovinný parametr. Pokud je zadán text, řádek je označen jako pojmenovaná zarážka. V opačném případě je řádek označen jako nepojmenovaná zarážka, což je podobné tomu, co se stane, když stisknete klávesu F9.

## <a name="example"></a>Příklad
Následující příklad přepíná aktuální zarážku.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
