---
title: Použití nástroje Finder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e92223359c6bc78b2a98c234c03ee139c052f86
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851837"
---
# <a name="how-to-use-the-finder-tool"></a>Postupy: Používání vyhledávacího nástroje
Pomocí nástroje Finder v dialogovém okně **Najít okno** můžete zobrazit vlastnosti nebo zprávy okna. Nástroj hledání může také najít zakázaná podřízená okna a nerozlišuje, které okno se má zvýraznit, pokud se zakázaná podřízená okna překrývají.

 ![Dialogová okna Najít okno pro Spy&#43;&#43; ](../debugger/media/icon_spy--_find.png "_Find Icon_Spy + +") Nástroj hledání v dialogovém okně Najít okno

 Výše uvedený obrázek ukazuje dialogové okno Najít okno hledání za krokem 3 níže.

### <a name="to-display-window-properties-or-messages"></a>Zobrazení vlastností nebo zpráv okna

1. Uspořádejte okna tak, aby se zobrazila okna Spy + + i cílové okno.

2. V nabídce **Spy** vyberte možnost **Najít okno**.

    Otevře se [dialogové okno Najít okno](../debugger/find-window-dialog-box.md) .

3. Přetáhněte **Nástroj hledání** přes cílové okno.

    Při přetahování nástroje se v dialogovém okně **Najít okno** zobrazí podrobnosti o vybraném okně.

   - ani

     Pokud máte popisovač okna, které chcete prošetřit (například zkopírované z ladicího programu), zadejte ho do textového pole **popisovač** .

   > [!TIP]
   > Pokud chcete omezit přehlednost obrazovky, vyberte možnost **Skrýt Spy** . Tato možnost zachová hlavní okno nástroje Spy + + a v horní části ostatních aplikací se zobrazí pouze dialogové okno **Najít okno** . Po kliknutí na tlačítko **OK** nebo **Zrušit**dojde k obnovení hlavního okna nástroje Spy + +, nebo když zrušíte zaškrtnutí políčka **Skrýt Spy + +** .

4. V části **Zobrazit**vyberte buď **vlastnosti** , nebo **zprávy**.

5. Stiskněte **OK**.

    Pokud jste vybrali **vlastnosti**, otevře se [dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md) . Pokud jste vybrali **zprávy**, otevře se okno [zobrazení zprávy](../debugger/messages-view.md) .

## <a name="see-also"></a>Viz také
- [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)
- [Použití nástroje Spy++](../debugger/using-spy-increment.md)
- [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)