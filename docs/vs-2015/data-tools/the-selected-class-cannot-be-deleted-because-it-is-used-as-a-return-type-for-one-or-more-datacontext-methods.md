---
title: Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro jednu nebo více metod DataContext | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 084843636d62bd7d85c5bbc141aa0fe8ddf81462
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236259"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Vybranou třídu nejde odstranit, protože se používá jako návratový typ pro minimálně jednu metodu DataContext.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Návratový typ jednoho nebo více <xref:System.Data.Linq.DataContext> metody je třída vybrané entity. Odstraňuje třídu entity, která se používá jako návratový typ <xref:System.Data.Linq.DataContext> způsobí, že metoda kompilace projektu selže. Pokud chcete odstranit vybrané entity třídy, identifikovat <xref:System.Data.Linq.DataContext> metody, které použije a nastavte typy vrácených hodnot na jiné entity třídy.  
  
 Obnova návratové typy <xref:System.Data.Linq.DataContext> metody do jejich původního automaticky vygenerovaných typů, odstraňte nejprve <xref:System.Data.Linq.DataContext> metoda z podokna metody a pak přetáhněte objekt z **Průzkumníka serveru** / **Průzkumník databáze** do Návrháře relací objektů znovu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Identifikace <xref:System.Data.Linq.DataContext> metody, které používají entity třídy jako návratový typ tak, že vyberete <xref:System.Data.Linq.DataContext> metody v rámci metod podokně a zkontrolujete **návratový typ** vlastnost v **vlastnosti** okno .  
  
2.  Nastavte **návratový typ** třída jiné entity nebo delete <xref:System.Data.Linq.DataContext> metoda z podokna metody.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Postupy: Změna návratového typu metody DataContext (Návrhář relací objektů)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

