---
title: Tato související metoda je záložní metoda pro následující výchozí vložení, aktualizace nebo odstranění metody | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 34c44a8d47ab1694b2af7accd76ef5432668a212
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259138"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Tato související metoda je záložní metoda pro následující výchozí metody vložení, aktualizace nebo odstranění.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tato související metoda je záložní metoda pro následující výchozí vložení, aktualizace nebo odstranění metody. Pokud se odstraní, odstraní se i tyto metody. Přejete si pokračovat?  
  
 Vybrané `DataContext` metoda se aktuálně používá jako jeden z metody Insert, Update nebo Delete pro jednu z tříd entit na Návrháře relací objektů. Odstranění vybrané metody třídy entity, která se pomocí této metody vrátit zpět k výchozímu chování za běhu pro provádění Insert, Update, nebo odstranit během aktualizace.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Chcete odstranit vybrané metody způsobí třídu entity aktualizace modulu runtime  
  
-   Klikněte na tlačítko **Ano**.  
  
     Odstraní vybranou metodu a všechny třídy, které používají tuto metodu pro přepsání nastavení aktualizace jsou vráceny pomocí výchozí LINQ na SQL chování za běhu.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Zavřete okno se zprávou, beze změny byste museli opustit vybrané metody  
  
-   Klikněte na tlačítko **ne**.  
  
     Zavře okno se zprávou a nebudou provedeny žádné změny.  
  
## <a name="see-also"></a>Viz také  
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

