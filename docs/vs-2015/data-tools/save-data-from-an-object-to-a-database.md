---
title: Uložení dat z objektu do databáze | Dokumentace Microsoftu
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: acbbf9f309573f110da3b7dd0a53ede36150a319
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207451"
---
# <a name="save-data-from-an-object-to-a-database"></a>Uložení dat z objektu do databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Předáním hodnoty z objektu do jednoho objektu TableAdapter dbdirect – metody můžete uložit data v objektech k databázi (například `TableAdapter.Insert`). Další informace najdete v tématu [TableAdapter – přehled](../data-tools/tableadapter-overview.md).  
  
 K uložení dat z kolekce objektů smyčky přes kolekce objektů (například smyčka pro další) a odešlete hodnoty pro každý objekt do databáze pomocí jedné z objektu TableAdapter dbdirect – metody.  
  
 Ve výchozím nastavení vytvářejí dbdirect – metody na objektu typu TableAdapter, který můžete spustit přímo proti databázi. Tyto metody lze volat přímo a nevyžadují <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> objekty sloučit změny k odeslání aktualizací do databáze.  
  
> [!NOTE]
>  Když konfigurujete TableAdapter, hlavního dotazu musí poskytnout dostatek informací pro dbdirect – metody, který se má vytvořit. Například pokud objektu TableAdapter je konfigurován pro dotazování na data z tabulky, která nemá sloupec primárního klíče definované, se nevygeneruje žádný dbdirect – metody.  
  
|TableAdapter dbdirect – metody|Popis|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožňuje vám a zajistěte tak předání hodnot jednotlivých sloupců jako parametry metod.|  
|`TableAdapter.Update`|Aktualizace existujících záznamů v databázi. `Update` Metoda má sloupec původní a nové hodnoty jako parametry metod. Původní hodnoty se používají pro vyhledání záznamu původní a nové hodnoty se používají k aktualizaci záznamu.<br /><br /> `TableAdapter.Update` Metoda slouží také k synchronizaci změn v datové sadě zpět do databáze pomocí <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, nebo pole <xref:System.Data.DataRow>označují jako parametry metody.|  
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze založené na původní hodnoty ve sloupcích předané jako parametry metod.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Chcete-li uložit nové záznamy z objektu do databáze  
  
-   Vytvořte záznamy předáním hodnoty tak, aby `TableAdapter.Insert` metody.  
  
     Následující příklad vytvoří nový záznam zákazníka v `Customers` předáním hodnoty v tabulce `currentCustomer` objektu `TableAdapter.Insert` metoda.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Chcete-li aktualizovat existující záznamy z objektu do databáze  
  
-   Upravit záznamy voláním `TableAdapter.Update` metody předáním v nových hodnotách aktualizovat záznam a předáním v původní hodnoty, které mají vyhledejte záznam.  
  
    > [!NOTE]
    >  Objekt je potřeba udržovat původní hodnoty. Chcete-li předat jim `Update` metody. Tento příklad používá vlastnosti `orig` předpona, která uložit původní hodnoty.  
  
     Následující příklad aktualizuje existující záznam v `Customers` předáním nových a původních hodnot v tabulce `Customer` objektu `TableAdapter.Update` metoda.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Můžete z databáze odstranit existující záznamy  
  
-   Odstranit záznamy voláním `TableAdapter.Delete` metoda a předáním původní hodnoty, které mají vyhledejte záznam.  
  
    > [!NOTE]
    >  Objekt je potřeba udržovat původní hodnoty. Chcete-li předat jim `Delete` metody. Tento příklad používá vlastnosti `orig` předpona, která uložit původní hodnoty.  
  
     Následující příklad odstraní záznam z `Customers` předáním původní hodnoty v tabulce `Customer` objektu `TableAdapter.Delete` metoda.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Musíte mít oprávnění k provádění vybraných INSERT, UPDATE nebo DELETE na tabulku v databázi.  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

