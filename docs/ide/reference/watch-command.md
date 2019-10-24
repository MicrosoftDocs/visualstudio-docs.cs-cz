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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 411452ba0cf8f8625ee67bca51c2f3735f6dc924
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747697"
---
# <a name="watch-command"></a>Kukátko – příkaz
Vytvoří a otevře zadanou instanci okna **kukátka** . Okno **kukátka** můžete použít k výpočtu hodnot proměnných, výrazů a registrů pro úpravu těchto hodnot a k uložení výsledků.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Arguments

`index`\
Požadováno. Číslo instance okna Kukátko.

## <a name="remarks"></a>Poznámky

@No__t_0 musí být celé číslo. Platné hodnoty jsou 1, 2, 3 nebo 4.

## <a name="example"></a>Příklad

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Viz také:

- [Okna automatických a místních hodnot](../../debugger/autos-and-locals-windows.md)
- [Nastavení sledování proměnných pomocí oken kukátka a QuickWatch v sadě Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)