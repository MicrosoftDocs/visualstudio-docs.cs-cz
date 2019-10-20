---
title: Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aff8d7c01291c410f81b00c689f600507841965b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640058"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.

Návratový typ jedné nebo více metod <xref:System.Data.Linq.DataContext> je vybraná třída entity. Odstranění třídy entity, která se používá jako návratový typ pro metodu <xref:System.Data.Linq.DataContext> způsobí, že se kompilace projektu nezdařila. Chcete-li odstranit vybranou třídu entity, identifikujte <xref:System.Data.Linq.DataContext> metody, které ji používají, a nastavte jejich návratové typy na jinou třídu entity.

Chcete-li vrátit návratové typy <xref:System.Data.Linq.DataContext> metody do jejich původních automaticky generovaných typů, nejprve odstraňte metodu <xref:System.Data.Linq.DataContext> z podokna **metody** a potom objekt přetáhněte z **Průzkumník serveru** /**Průzkumník databáze** na hodnotu **o/R. Návrhář** znovu.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Identifikujte <xref:System.Data.Linq.DataContext> metody, které používají třídu entity jako návratový typ, výběrem metody <xref:System.Data.Linq.DataContext> v podokně **metody** a kontrolou vlastnosti **návratového typu** v okně **vlastnosti** .

2. Nastavte **návratový typ** na jinou třídu entity nebo odstraňte metodu <xref:System.Data.Linq.DataContext> z podokna metody.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)