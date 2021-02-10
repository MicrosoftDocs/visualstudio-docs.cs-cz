---
title: Rychlé kukátko – příkaz
description: Přečtěte si o příkazu Rychlé kukátko a způsobu zobrazení vybraného nebo zadaného textu v poli Expression okna QuickWatch.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5557fb9ca4c362f764cac04441add4fea0433856
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958190"
---
# <a name="quick-watch-command"></a>Rychlé kukátko – příkaz
Zobrazí vybraný nebo zadaný text v poli Expression okna [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) . Toto dialogové okno můžete použít k výpočtu aktuální hodnoty proměnné nebo výrazu rozpoznaného ladicím programem nebo obsahu registru. Kromě toho můžete změnit hodnotu libovolné nekonstantní proměnné nebo obsah jakéhokoli registru.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty

`text`\
Nepovinný parametr. Text, který se má přidat do dialogového okna **QuickWatch** .

## <a name="remarks"></a>Poznámky

Pokud `text` je tento parametr vynechán, je aktuálně vybraný text nebo slovo na kurzoru přidáno do okno kukátko.

## <a name="example"></a>Příklad

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Viz také

- [Nastavení sledování proměnných pomocí oken kukátka a QuickWatch v sadě Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
