---
title: Tato související metoda je metoda zálohování pro následující výchozí metody vložení, aktualizace nebo odstranění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667185"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Tato související metoda je záložní metoda pro následující výchozí metody vložení, aktualizace nebo odstranění.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato související metoda je metoda zálohování pro následující výchozí metody vložení, aktualizace nebo odstranění. Pokud se odstraní, odstraní se i tyto metody. Přejete si pokračovat?

 Vybraná metoda `DataContext` se aktuálně používá jako jedna z metod INSERT, Update nebo DELETE pro jednu z tříd entit v Návrháři O/R. Odstraněním vybrané metody dojde k tomu, že třída entity, která byla použita touto metodou, se vrátí k výchozímu chování za běhu za účelem provedení operace INSERT, Update nebo DELETE během aktualizace.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Odstranění vybrané metody, což způsobí, že třída entity bude používat aktualizace za běhu

- Klikněte na tlačítko **Ano**.

     Vybraná metoda je odstraněna a všechny třídy, které použily tuto metodu pro přepsání chování aktualizace, budou vráceny na použití výchozího chování LINQ to SQL runtime.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Chcete-li zavřít okno se zprávou, nechte vybranou metodu beze změny.

- Klikněte na tlačítko **ne**.

     Okno se zprávou se zavře a nebudou provedeny žádné změny.

## <a name="see-also"></a>Viz také
 [Metody DataContext (O/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (o/r Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL nástrojů v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
