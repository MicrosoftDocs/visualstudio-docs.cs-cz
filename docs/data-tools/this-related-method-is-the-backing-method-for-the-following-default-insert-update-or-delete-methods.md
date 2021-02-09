---
title: Nejde odstranit metodu zálohování.
description: Tato související metoda je záložní metoda pro následující výchozí metody vložení, aktualizace nebo odstranění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 94e9f1f91aa5c879e0e3ed0034e0d1f554901513
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866369"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Tato související metoda je záložní metoda pro následující výchozí metody vložení, aktualizace nebo odstranění.

Tato související metoda je metoda zálohování pro následující výchozí `Insert` `Update` metody, nebo `Delete` . Pokud se odstraní, odstraní se i tyto metody. Chcete pokračovat?

Vybraná `DataContext` Metoda je aktuálně používána jako jedna z `Insert` `Update` metod, nebo `Delete` pro jednu z tříd entity v **Návrháři o/R**. Odstraněním vybrané metody dojde k tomu, že třída entity, která byla použita touto metodou, se vrátí k výchozímu chování za běhu pro provedení operace INSERT, Update nebo DELETE během aktualizace.

## <a name="selected-method-options"></a>Vybrané možnosti metody

- Chcete-li odstranit vybranou metodu, což způsobí, že třída entity bude používat aktualizace modulu runtime, klikněte na tlačítko **Ano**.

   Vybraná metoda je odstraněna a všechny třídy, které použily tuto metodu pro přepsání chování aktualizace, budou vráceny na použití výchozího LINQ to SQL chování za běhu.

- Chcete-li zavřít okno se zprávou a vybranou metodu ponechat beze změny, klikněte na tlačítko **ne**.

   Okno se zprávou se zavře a nebudou provedeny žádné změny.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)