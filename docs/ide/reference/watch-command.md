---
title: Kukátko – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7c89761dfc12d342747567389e39daeed4a227
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585649"
---
# <a name="watch-command"></a>Kukátko – příkaz
Vytvoří a otevře zadanou instanci okna **Kukátka.** Okno **Kukátko** můžete použít k výpočtu hodnot proměnných, výrazů a registrů, k úpravě těchto hodnot a k uložení výsledků.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty

`index`\
Povinná hodnota. Číslo instance okna kukátka.

## <a name="remarks"></a>Poznámky

Musí `index` být celé číslo. Platné hodnoty jsou 1, 2, 3 nebo 4.

## <a name="example"></a>Příklad

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Viz také

- [Okna automatických a místních hodnot](../../debugger/autos-and-locals-windows.md)
- [Nastavení sledování proměnných pomocí hodinek a rychlých hodinproWindows v sadě Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
