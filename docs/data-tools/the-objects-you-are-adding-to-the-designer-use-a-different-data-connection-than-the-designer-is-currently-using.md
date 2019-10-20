---
title: Objekty přidané do návrháře používají jiné datové připojení.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 915860c2559335f37869f5c6009f7a38dde6abcd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640846"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Objekty, které přidáváte do návrháře, používají jiné datové připojení než Návrhář.

Objekty, které přidáváte do návrháře, používají jiné datové připojení než Návrhář aktuálně používá. Chcete nahradit připojení používané návrhářem?

Když přidáte položky do **Návrhář relací objektů** (**Návrhář O/R**), budou všechny položky používat jedno sdílené datové připojení. (Návrhová plocha představuje <xref:System.Data.Linq.DataContext>, která používá jedno připojení pro všechny objekty na povrchu.) Pokud přidáte objekt do návrháře, který používá datové připojení, které se liší od datového připojení, které je aktuálně používáno návrhářem, zobrazí se tato zpráva. Tuto chybu můžete vyřešit tak, že se rozhodnete zachovat stávající připojení. Pokud uděláte tuto volbu, vybraný objekt se nepřidá. Alternativně můžete zvolit přidání objektu a resetování <xref:System.Data.Linq.DataContext> připojení k novému připojení.

## <a name="connection-options"></a>Možnosti připojení

- Pokud chcete stávající připojení nahradit připojením použitým pro vybraný objekt, klikněte na **Ano**.

   Vybraný objekt je přidán k Návrháři pro **/R**a *DataContext. připojení* je nastaveno na nové připojení.

   > [!NOTE]
   > Kliknete-li na tlačítko **Ano**, všechny třídy entit v **Návrháři o/R** jsou namapovány na nové připojení.

- Chcete-li nadále používat existující připojení a zrušit přidávání vybraného objektu, klikněte na tlačítko **ne**.

   Akce se zrušila. *Kontext DataContext. připojení* zůstává nastaveno na existující připojení.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
