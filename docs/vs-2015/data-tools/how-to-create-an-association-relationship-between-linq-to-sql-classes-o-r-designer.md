---
title: 'Postupy: vytvoření přidružení (vztah) mezi třídy LINQ to SQL (O R Designer) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c739fcf11cec7eb841b99e58b01ada32cfdfd49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209362"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Postupy: vytvoření přidružení (vztah) mezi třídy LINQ to SQL (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Přidružení mezi třídami entit v [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] jsou podobná relace mezi tabulkami v databázi. Můžete vytvořit přidružení mezi třídami entit pomocí **Editor asociace** dialogové okno.  
  
 Při použití musíte vybrat třídu nadřazené a podřízené třídy **Editor asociace** dialogové okno Vytvoření přidružení. Nadřazená třída je třída entity, která obsahuje primární klíč. podřízené třídy je třída entity, která obsahuje cizího klíče. Například pokud tříd entit byly vytvořeny, která je namapována na tabulky Northwind zákazníci a objednávky, zákazník třídy by nadřazené třídy a třídy pořadí by podřízené třídy.  
  
> [!NOTE]
>  Při přetažení tabulky z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), jsou automaticky vytvořeny podle existující přidružení vztahy cizího klíče v databázi.  
  
 Po vytvoření asociace, když vyberete přidružení v O/R Designer, existuje několik konfigurovatelných vlastností v **vlastnosti** okna. (Přidružení je řádek mezi souvisejícími třídami.) Následující tabulka obsahuje popis vlastností asociace.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Kardinalita**|Určuje, zda že asociace je 1 n nebo 1: 1.|  
|**Podřízená vlastnost**|Určuje, jestli se má vytvořit vlastnost u nadřazené, který je kolekce nebo odkaz na podřízené záznamy na straně cizího klíče asociace. Například v přidružení mezi odběratele a objednávky Pokud **vlastnost podřízeného** je nastavena na **True**, se vytvoří vlastnost s názvem objednávky na nadřazené třídy.|  
|**Nadřazená vlastnost**|Vlastnost u podřízené třídy, která odkazuje na přidruženou nadřazenou třídu. Například v přidružení mezi odběratele a objednávky, se vytvoří vlastnost s názvem zákazníka, který odkazuje na související zákazníka objednávky ve třídě pořadí.|  
|**Zúčastněné vlastnosti**|Zobrazí vlastnosti přidružení a poskytuje **tlačítko se třemi tečkami** tlačítko (...), která znovu se otevře **Editor asociace** dialogové okno.|  
|**Jedinečný**|Určuje, jestli mají sloupce cizího omezení jedinečnosti.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>Vytvoření přidružení mezi třídami entit  
  
1.  Klikněte pravým tlačítkem na třídu entity, která představuje nadřazené třídu v přidružení, přejděte na **přidat**a potom klikněte na tlačítko **přidružení**.  
  
2.  Ověřte, že správné **nadřazené třídu** výběru v **Editor asociace** dialogové okno.  
  
3.  Vyberte **podřízené třídy** v poli se seznamem.  
  
4.  Vyberte **vlastnosti přidružení** , které se týkají třídy. Obvykle to se mapuje na vztah cizího klíče definovanými v databázi. Například v přidružení zákazníci a objednávky **vlastnosti přidružení** jsou CustomerID pro každou třídu.  
  
5.  Klikněte na tlačítko **OK** vytváření přidružení.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Postupy: Znázornění primárních klíčů](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

