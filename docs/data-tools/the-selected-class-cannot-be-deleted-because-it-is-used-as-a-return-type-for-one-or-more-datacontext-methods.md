---
title: Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: faea45cc7198be91a45d0bb57a62ce2730011ee2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281328"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.

Návratový typ jedné nebo více <xref:System.Data.Linq.DataContext> metod je vybraná třída entity. Odstranění třídy entity, která se používá jako návratový typ pro <xref:System.Data.Linq.DataContext> metodu způsobí selhání kompilace projektu. Chcete-li odstranit vybranou třídu entity, identifikujte <xref:System.Data.Linq.DataContext> metody, které ji používají, a nastavte jejich návratové typy na jinou třídu entity.

Chcete-li vrátit návratové typy <xref:System.Data.Linq.DataContext> metod do jejich původních automaticky generovaných typů, nejprve odstraňte <xref:System.Data.Linq.DataContext> metodu z podokna **metody** a pak objekt přetáhněte z **Průzkumník serveru** / **Průzkumník databáze** do **návrháře pro/R** .

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Identifikujte <xref:System.Data.Linq.DataContext> metody, které používají třídu entity jako návratový typ, výběrem <xref:System.Data.Linq.DataContext> metody v podokně **metody** a kontrolou vlastnosti **návratového typu** v okně **vlastnosti** .

2. Nastavte **návratový typ** na jinou třídu entity nebo odstraňte <xref:System.Data.Linq.DataContext> metodu z podokna metody.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
