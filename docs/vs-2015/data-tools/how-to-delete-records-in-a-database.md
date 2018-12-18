---
title: 'Postupy: odstranění záznamů v databázi | Dokumentace Microsoftu'
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
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 87ab5ccde2c1100fbd0efc5f4272efe27803b717
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938614"
---
# <a name="how-to-delete-records-in-a-database"></a>Postupy: Odstranění záznamů z databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete z databáze odstranit záznamy, použít `TableAdapter.Update` metoda nebo `TableAdapter.Delete` metody. Nebo, pokud vaše aplikace nepoužívá objekty TableAdapter, můžete použít objekty příkazu k odstranění záznamů z databáze (například <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 `TableAdapter.Update` Metoda se typicky používá, když vaše aplikace používá k ukládání dat, datové sady vzhledem k tomu `TableAdapter.Delete` metoda se typicky používá, když vaše aplikace používá k ukládání dat objektů.  
  
 Pokud vaše TableAdapter nemá `Delete` metoda, znamená to buď objektu TableAdapter je nakonfigurován na použití uložených procedur, nebo jeho `GenerateDBDirectMethods` je nastavena na `false`. Nastavte TableAdapter `GenerateDBDirectMethods` vlastnost `true` v rámci [Návrhář Dataset](../data-tools/creating-and-editing-typed-datasets.md) a uložte datovou sadu znovu vygenerovat TableAdapter. V případě TableAdapter ještě není `Delete` metodu a poté v tabulce pravděpodobně neposkytuje dostatek informací o schématu rozlišovat mezi jednotlivé řádky (například žádný primární klíč je nastavený v tabulce).  
  
## <a name="delete-records-using-tableadapters"></a>Odstraňovat záznamy pomocí objektů TableAdapter  
 Objekty TableAdapter umožňují různými způsoby pro odstranění záznamů z databáze v závislosti na požadavcích vaší aplikace.  
  
 Pokud vaše aplikace používá k ukládání dat datové sady můžete jednoduše odstranit záznamy z požadovaný <xref:System.Data.DataTable> v <xref:System.Data.DataSet>a následně zavolat `TableAdapter.Update` metody. `TableAdapter.Update` Metoda přijímá všechny změny v tabulce dat a odesílá tyto změny do databáze (včetně vložené, aktualizované a odstraněné záznamy).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Chcete-li odstranit záznamy v databázi pomocí TableAdapter.Update – metoda  
  
- Odstranění záznamů z požadovaný <xref:System.Data.DataTable> odstraněním <xref:System.Data.DataRow> objekty z tabulky. Další informace najdete v tématu [postupy: odstranění řádků z DataTable](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Po odstranění řádků z <xref:System.Data.DataTable>, zavolejte `TableAdapter.Update` metody. Můžete řídit objem dat se aktualizovat předáním celý <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, pole <xref:System.Data.DataRow>s nebo jediný <xref:System.Data.DataRow>. Následující kód ukazuje, jak odstranit záznam z <xref:System.Data.DataTable> a následně zavolat `TableAdapter.Update` metodu pro komunikaci změnu a z databáze odstranit řádek. (Tento příklad používá databázi Northwind `Region` tabulky.)  
  
   [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
   [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
  Pokud vaše aplikace používá objekty k uložení dat v aplikaci, můžete přímo z databáze odstranit data objektu TableAdapter dbdirect – metody. Volání `Delete` metoda odebere záznamy z databáze na základě hodnot parametru předaného.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Chcete-li odstranit záznamy v databázi pomocí TableAdapter.delete – metoda  
  
-   Volání objektu TableAdapter `Delete` metodu předáním hodnoty pro každý sloupec jako parametry `Delete` metody. (Tento příklad používá databázi Northwind `Region` tabulky.)  
  
    > [!NOTE]
    >  Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, které chcete použít.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Odstraňovat záznamy pomocí příkazu objektů  
 Následující příklad odstraní záznamy přímo z databáze pomocí příkazu objektů. Další informace o používání objektů příkazu ke spuštění příkazů a uložených procedur, naleznete v tématu [načítání dat do aplikace](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Odstranit záznamy z databáze pomocí příkazu objektů  
  
-   Vytvořit nový objekt příkazu, nastavte jeho `Connection`, `CommandType`, a `CommandText` vlastnosti. (Tento příklad používá databázi Northwind `Region` tabulky.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Musíte mít přístup k databázi, kterou se pokoušíte připojit k, jakož i oprávnění k odstranění záznamů z požadovanou tabulku.  
  
## <a name="see-also"></a>Viz také  
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Vkládání nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md)   
 [Postupy: aktualizace záznamů v databázi](../data-tools/how-to-update-records-in-a-database.md)   
 [Uložení dat z objektu do databáze](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Přehled datových aplikacích v sadě Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)