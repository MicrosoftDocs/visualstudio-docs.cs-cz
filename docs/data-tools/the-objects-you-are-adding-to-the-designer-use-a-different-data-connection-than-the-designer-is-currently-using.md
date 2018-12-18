---
title: Objekty, které přidáváte do návrháře, obsahují jiné datové připojení než připojení momentálně používané návrhářem.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a2fb26fa8960c652feefa157fb04c31b9ed7abb9
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174189"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Objekty, které přidáváte do návrháře použít odlišné datové připojení než návrháře

Objekty, které přidáváte do návrháře použijte odlišné datové připojení, než momentálně používané návrhářem. Opravdu chcete připojení používané návrhářem nahradit?

Při přidávání položek do **Návrhář relací objektů** (**O/R Designer**), všech položek se používají sdílené datové připojení. (Na návrhovou plochu představuje <xref:System.Data.Linq.DataContext>, který používá jedno připojení pro všechny objekty na povrchu.) Pokud chcete přidat objekt do návrháře, který používá datové připojení, které se liší od aktuálně používá v Návrháři datové připojení, tato zpráva se zobrazí. Chcete-li vyřešit tuto chybu, můžete zachovat existující připojení. Pokud tuto volbu, nebude přidán vybraný objekt. Alternativně můžete přidat objekt a obnovit <xref:System.Data.Linq.DataContext> připojení k nové připojení.

> [!NOTE]
> Vyberete-li **Ano**, tříd na všech entit **O/R Designer** jsou mapovány na nového připojení.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Chcete-li nahradit stávající připojení pomocí připojení používané objektem vybraný objekt

- Klikněte na tlačítko **Ano**.

    Vybraný objekt se přidá do **O/R Designer**a *DataContext.Connection* je nastavena na nové připojení.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Chcete-li nadále používat stávající připojení a zrušit přidávání vybraný objekt

- Klikněte na tlačítko **ne**.

    Akce zrušena. *DataContext.Connection* zůstane nastavena na existující připojení.

## <a name="see-also"></a>Viz také:

- [Zprávy Návrháře relací objektů](../data-tools/o-r-designer-messages.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
