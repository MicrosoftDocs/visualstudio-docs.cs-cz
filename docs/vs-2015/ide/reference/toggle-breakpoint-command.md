---
title: Přepnout zarážku – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25c9a22db7ae136068ec374f874453dbd4a7c4b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658622"
---
# <a name="toggle-breakpoint-command"></a>Přepnout zarážku – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zapne nebo vypne zarážku v závislosti na jejím aktuálním stavu, a to v aktuálním umístění v souboru.

## <a name="syntax"></a>Syntaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumenty
 `text` Volitelné. Je-li zadán text, je řádek označen jako pojmenovaná zarážka. V opačném případě je řádek označený jako Nepojmenovaná zarážka, což se podobá tomu, co se stane po stisknutí klávesy F9.

## <a name="example"></a>Příklad
 Následující příklad přepíná aktuální zarážku.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
