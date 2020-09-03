---
title: Vybranou třídu nelze odstranit, protože se používá jako návratový typ pro jednu nebo více metod DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667261"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návratový typ jedné nebo více <xref:System.Data.Linq.DataContext> metod je vybraná třída entity. Odstranění třídy entity, která se používá jako návratový typ pro <xref:System.Data.Linq.DataContext> metodu způsobí, že dojde k selhání kompilace projektu. Chcete-li odstranit vybranou třídu entity, identifikujte <xref:System.Data.Linq.DataContext> metody, které ji používají, a nastavte jejich návratové typy na jinou třídu entity.

 Chcete-li vrátit návratové typy <xref:System.Data.Linq.DataContext> metod do jejich původních automaticky generovaných typů, nejprve odstraňte <xref:System.Data.Linq.DataContext> metodu z podokna metody a pak objekt přetáhněte z **Průzkumník serveru** / **Průzkumník databáze** do návrháře pro/R.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Identifikujte <xref:System.Data.Linq.DataContext> metody, které používají třídu entity jako návratový typ, výběrem <xref:System.Data.Linq.DataContext> metody v podokně metody a kontrolou vlastnosti **návratového typu** v okně **vlastnosti** .

2. Nastavte **návratový typ** na jinou třídu entity nebo odstraňte <xref:System.Data.Linq.DataContext> metodu z podokna metody.

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– návod: vytváření LINQ to SQL tříd (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [metod DataContext (o/r Designer](../data-tools/datacontext-methods-o-r-designer.md) ) [Postupy: Změna návratového typu metody DataContext (o/r Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
