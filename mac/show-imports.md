---
title: Zobrazit položky importu
description: Pomocí zobrazit položky importu rozbalíte IntelliSense v Visual Studio pro Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451508"
---
# <a name="show-import-items"></a>Zobrazit položky importu

Visual Studio pro Mac může zobrazit všechny dostupné typy i v případě, že nejsou naimportovány do projektu, v seznamu dokončení IntelliSense. Když vyberete položku, která není naimportovaná, do `using` zdrojového souboru se přidá správný příkaz.

![Zobrazit přehled položek importu](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Jak povolit

Pokud chcete tuto funkci povolit, otevřete **Předvolby** přes předvolby sady **Visual Studio**  >  **Preferences** a přejděte na **textový editor**  >  **IntelliSense**. Zaškrtněte pole **Zobrazit položky importu** a povolte tak další položky v IntelliSense.

![Zobrazit položku Import položek](media/show-import-items.png)

## <a name="usage"></a>Využití

Jakmile povolíte možnost **Zobrazit položky importu**, proces použití funkce pro import položky je podobný běžným akcím v rámci technologie IntelliSense. Při psaní kódu naplní položky, které jsou platné, seznam dokončení. Sem patří položky, které ještě nebyly naimportovány. Položky, které nejsou naimportovány, zobrazí jejich úplný obor názvů napravo od položky, což vám umožní zjistit, které importy do projektu nasazujete.

![Zobrazit seznam položek importu](media/show-import-items-list.png)

V seznamu technologie IntelliSense jsou obory názvů zobrazeny vedle členů, kteří nejsou aktuálně odkazováni `using` příkazem. Pokud zvolíte jednu z těchto položek ze seznamu, člen se přidá do vašeho kódu _a_ `using` příkaz se přidá do horní části souboru. Členy z typů, které již jsou odkazovány v kódovaném kódu, nebudou v technologii IntelliSense zobrazovat jejich obor názvů.

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoring kódu (Visual Studio ve Windows)](/visualstudio/ide/refactoring-in-visual-studio)
