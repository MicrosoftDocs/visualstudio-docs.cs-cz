---
title: Tato související metoda je záložní metoda pro následující výchozí metody vložení, aktualizace nebo odstranění.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 11c5c7d3c8078aa420074e9e32bb132489b169c8
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252947"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Tato související metoda je záložní metoda pro následující výchozí metody vložení, aktualizace nebo odstranění.

Tato související metoda je metoda zálohování pro následující výchozí `Insert`metody, `Update`nebo `Delete` . Pokud se odstraní, odstraní se i tyto metody. Přejete si pokračovat?

Vybraná `DataContext` metoda je aktuálně používána jako jedna `Insert`z metod, `Update`nebo `Delete` pro jednu z tříd entity v **Návrháři o/R**. Odstraněním vybrané metody dojde k tomu, že třída entity, která byla použita touto metodou, se vrátí k výchozímu chování za běhu pro provedení operace INSERT, Update nebo DELETE během aktualizace.

## <a name="selected-method-options"></a>Vybrané možnosti metody

- Chcete-li odstranit vybranou metodu, což způsobí, že třída entity bude používat aktualizace modulu runtime, klikněte na tlačítko **Ano**.

   Vybraná metoda je odstraněna a všechny třídy, které použily tuto metodu pro přepsání chování aktualizace, budou vráceny na použití výchozího LINQ to SQL chování za běhu.

- Chcete-li zavřít okno se zprávou a vybranou metodu ponechat beze změny, klikněte na tlačítko **ne**.

   Okno se zprávou se zavře a nebudou provedeny žádné změny.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)