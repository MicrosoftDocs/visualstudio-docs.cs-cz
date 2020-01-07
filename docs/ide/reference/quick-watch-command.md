---
title: Rychlé kukátko – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f6382a79884bf8c3891a3a191b594bf183efb62
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565627"
---
# <a name="quick-watch-command"></a>Rychlé kukátko – příkaz
Zobrazí vybraný nebo zadaný text v poli Expression okna [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) . Toto dialogové okno můžete použít k výpočtu aktuální hodnoty proměnné nebo výrazu rozpoznaného ladicím programem nebo obsahu registru. Kromě toho můžete změnit hodnotu libovolné nekonstantní proměnné nebo obsah jakéhokoli registru.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments

`text`\
Volitelné. Text, který se má přidat do dialogového okna **QuickWatch** .

## <a name="remarks"></a>Poznámky

Pokud je hodnota `text` vynechána, je aktuálně vybraný text nebo slovo na kurzoru přidáno do okno Kukátko.

## <a name="example"></a>Příklad

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Viz také:

- [Nastavení sledování proměnných pomocí oken kukátka a QuickWatch v sadě Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
