---
title: Vybranou třídu nelze odstranit.
description: Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9948df37df4faf7cc5349b2729ca4f648d973cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866382"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.

Návratový typ jedné nebo více <xref:System.Data.Linq.DataContext> metod je vybraná třída entity. Odstranění třídy entity, která se používá jako návratový typ pro <xref:System.Data.Linq.DataContext> metodu způsobí selhání kompilace projektu. Chcete-li odstranit vybranou třídu entity, identifikujte <xref:System.Data.Linq.DataContext> metody, které ji používají, a nastavte jejich návratové typy na jinou třídu entity.

Chcete-li vrátit návratové typy <xref:System.Data.Linq.DataContext> metod do jejich původních automaticky generovaných typů, nejprve odstraňte <xref:System.Data.Linq.DataContext> metodu z podokna **metody** a pak objekt přetáhněte z **Průzkumník serveru** / **Průzkumník databáze** do **návrháře pro/R** .

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Identifikujte <xref:System.Data.Linq.DataContext> metody, které používají třídu entity jako návratový typ, výběrem <xref:System.Data.Linq.DataContext> metody v podokně **metody** a kontrolou vlastnosti **návratového typu** v okně **vlastnosti** .

2. Nastavte **návratový typ** na jinou třídu entity nebo odstraňte <xref:System.Data.Linq.DataContext> metodu z podokna metody.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
