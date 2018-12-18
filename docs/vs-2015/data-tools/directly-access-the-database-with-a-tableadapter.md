---
title: Přímý přístup k databázi pomocí TableAdapter | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a592a185ad3dd01f881526e0b9471e3f5e969a94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178448"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Přímý přístup k databázi pomocí objektu TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Kromě `InsertCommand`, `UpdateCommand`, a `DeleteCommand`, jsou objekty TableAdapter vytvořeny metodami, které lze spustit přímo proti databázi. Tyto metody (`TableAdapter.Insert`, `TableAdapter.Update`, a `TableAdapter.Delete`) lze volat pro manipulaci s daty přímo v databázi.  
  
 Pokud tyto přímé metody vytvořit nechcete, nastavte TableAdapter `GenerateDbDirectMethods` vlastnost `false` v **vlastnosti** okna. Pokud přidáte všechny dotazy objektu TableAdapter kromě hlavním dotazem objektu TableAdapter jsou samostatné dotazy, které negenerovat tyto dbdirect – metody.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly k databázi  
 Volání metody třídy TableAdapter dbdirect –, který provádí úlohu, kterou se pokoušíte provést.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Chcete-li vkládání nových záznamů přímo do databáze  
  
-   Volání objektu TableAdapter `Insert` metodu předáním hodnoty pro každý sloupec jako parametry. Následující postup používá `Region` tabulku v Northwind databaseas příklad.  
  
    > [!NOTE]
    >  Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, který chcete použít.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>K aktualizaci záznamů přímo do databáze  
  
-   Volání objektu TableAdapter `Update` předejte jako původní a nové hodnoty pro každý sloupec jako parametry.  
  
    > [!NOTE]
    >  Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, který chcete použít.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Můžete přímo z databáze odstranit záznamy  
  
-   Volání objektu TableAdapter `Delete` metodu předáním hodnoty pro každý sloupec jako parametry `Delete` metody. Následující postup používá `Region` tabulku v Northwind databaseas příklad.  
  
    > [!NOTE]
    >  Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, který chcete použít.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také  
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

