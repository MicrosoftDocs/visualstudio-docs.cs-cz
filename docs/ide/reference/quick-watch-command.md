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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565627"
---
# <a name="quick-watch-command"></a>Rychlé kukátko – příkaz
Zobrazí vybraný nebo zadaný text v poli Výraz v okně [QuickWatch.](../../debugger/watch-and-quickwatch-windows.md) Toto dialogové okno můžete použít k výpočtu aktuální hodnoty proměnné nebo výrazu rozpoznaného ladicím programem nebo obsahu registru. Kromě toho můžete změnit hodnotu libovolné proměnné, která není const, nebo obsah libovolného registru.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty

`text`\
Nepovinný parametr. Text, který chcete přidat do dialogového okna **QuickWatch.**

## <a name="remarks"></a>Poznámky

Pokud `text` je vynechán, aktuálně vybraný text nebo slovo na kurzoru je přidán do okna Kukátko.

## <a name="example"></a>Příklad

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Viz také

- [Nastavení sledování proměnných pomocí hodinek a rychlých hodinproWindows v sadě Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
