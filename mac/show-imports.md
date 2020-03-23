---
title: Zobrazit položky importu
description: Pomocí možnosti Zobrazit importovat položky rozbalte technologie IntelliSense v Visual Studiu pro Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451508"
---
# <a name="show-import-items"></a>Zobrazit položky importu

Visual Studio pro Mac může v seznamu dokončení technologie IntelliSense zobrazit všechny dostupné typy, i když se do vašeho projektu neimportují. Výběrem položky, která není importována, bude do zdrojového souboru přidán správný `using` příkaz.

![zobrazit přehled položek importu](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Jak povolit

Chcete-li tuto funkci povolit, otevřete **předvolby** prostřednictvím**předvoleb** **sady Visual Studio** > a přejděte na **textovou editorovou** > **položku IntelliSense**. Zaškrtněte políčko **Zobrazit položky importu,** chcete-li v intelliSense povolit další položky.

![zobrazit možnost importu položek](media/show-import-items.png)

## <a name="usage"></a>Využití

Jakmile povolíte **možnost Zobrazit import položek**, proces použití této funkce k importu položky se podobá běžným akcím v aplikaci IntelliSense. Při psaní kódu budou platné položky naplněny seznamem dokončení. To zahrnuje položky, které ještě nebyly importovány. Položky, které nejsou importovány, zobrazí svůj úplný obor názvů napravo od položky, což vám umožní zjistit, které importy do projektu vytahujete.

![zobrazit seznam položek importu](media/show-import-items-list.png)

V seznamu IntelliSense jsou názvové prostory zobrazeny vedle členů, `using` na které aktuálně neodkazuje příkaz. Pokud zvolíte jednu z těchto položek ze seznamu, _and_ člen `using` bude přidán do vašeho kódu a příkaz bude přidán do horní části souboru. Členové z typů, na které se již odkazuje v kódovaném kódu, nezobrazí svůj obor názvů v inteligentním kódu IntelliSense.

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoringový kód (Visual Studio v systému Windows)](/visualstudio/ide/refactoring-in-visual-studio)
