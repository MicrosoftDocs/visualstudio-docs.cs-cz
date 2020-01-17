---
title: Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 249a5338985983509f04e0ff268b2f30e2773f71
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113558"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.

Návratový typ jedné nebo více metod <xref:System.Data.Linq.DataContext> je vybraná třída entity. Odstranění třídy entity, která se používá jako návratový typ pro metodu <xref:System.Data.Linq.DataContext> způsobí, že se kompilace projektu nezdařila. Chcete-li odstranit vybranou třídu entity, identifikujte <xref:System.Data.Linq.DataContext> metody, které ji používají, a nastavte jejich návratové typy na jinou třídu entity.

Chcete-li vrátit návratové typy <xref:System.Data.Linq.DataContext> metody do jejich původních automaticky generovaných typů, nejprve odstraňte metodu <xref:System.Data.Linq.DataContext> z podokna **metody** a pak objekt přetáhněte z **Průzkumník serveru**/**Průzkumník databáze** do **Návrháře relací** objektů.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Identifikujte <xref:System.Data.Linq.DataContext> metody, které používají třídu entity jako návratový typ, výběrem metody <xref:System.Data.Linq.DataContext> v podokně **metody** a kontrolou vlastnosti **návratového typu** v okně **vlastnosti** .

2. Nastavte **návratový typ** na jinou třídu entity nebo odstraňte metodu <xref:System.Data.Linq.DataContext> z podokna metody.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
