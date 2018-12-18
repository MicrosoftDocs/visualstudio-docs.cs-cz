---
title: Vkládání nových záznamů do databáze | Dokumentace Microsoftu
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9613d154cd0d9bb307fbde6d7255a8f1ecce000
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891470"
---
# <a name="insert-new-records-into-a-database"></a>Vkládání nových záznamů do databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vkládání nových záznamů do databáze, můžete `TableAdapter.Update` metody nebo jeden z objektu TableAdapter dbdirect – metody (konkrétně `TableAdapter.Insert` metoda). Další informace najdete v tématu [TableAdapter – přehled](../data-tools/tableadapter-overview.md).  
  
 Pokud vaše aplikace nepoužívá objekty TableAdapter, můžete použít příkaz objektů (například <xref:System.Data.SqlClient.SqlCommand>) pro vkládání nových záznamů do databáze.  
  
 Pokud vaše aplikace používá k ukládání dat datové sady, použijte `TableAdapter.Update` metody. `Update` Metoda odešle všechny změny (aktualizací, vložení a odstranění) do databáze.  
  
 Pokud vaše aplikace používá objekty k ukládání dat, nebo pokud chcete lepší kontrolu nad vytváření nových záznamů v databázi, použijte `TableAdapter.Insert` metody.  
  
 Pokud vaše TableAdapter nemá `Insert` metoda, znamená to, že buď objektu TableAdapter je nakonfigurován na použití uložené procedury nebo jeho `GenerateDBDirectMethods` je nastavena na `false`. Nastavte TableAdapter `GenerateDBDirectMethods` vlastnost `true` v rámci [Návrhář Dataset](../data-tools/creating-and-editing-typed-datasets.md)a potom uložte datovou sadu. Tímto se znova vygeneruje TableAdapter. Pokud TableAdapter stále nemá `Insert` metodu a poté v tabulce pravděpodobně neposkytuje dostatek informací o schématu rozlišovat mezi jednotlivé řádky (například může existovat žádná sada je primární klíče v tabulce).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Vkládání nových záznamů pomocí objektů TableAdapter  
 Objekty TableAdapter umožňují různé způsoby vkládání nových záznamů do databáze, v závislosti na požadavcích vaší aplikace.  
  
 Pokud vaše aplikace používá k ukládání dat datové sady, pak můžete jednoduše přidat nové záznamy na požadovaný <xref:System.Data.DataTable> datovou sadu, a poté zavolejte `TableAdapter.Update` metody. `TableAdapter.Update` Metoda odešle všechny změny v <xref:System.Data.DataTable> k databázi (včetně upravené a odstraněné záznamy).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Chcete-li vkládání nových záznamů do databáze s použitím TableAdapter.Update – metoda  
  
1. Přidání nových záznamů do požadované <xref:System.Data.DataTable> vytvořením nového <xref:System.Data.DataRow> a jejím přidáním na <xref:System.Data.DataTable.Rows%2A> kolekce. Další informace najdete v tématu [postupy: Přidání řádků do DataTable určitého](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2. Po přidání nových řádků do <xref:System.Data.DataTable>, zavolejte `TableAdapter.Update` metody. Můžete řídit objem dat se aktualizovat předáním buď celý <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, pole <xref:System.Data.DataRow>s nebo jediný <xref:System.Data.DataRow>.  
  
    Následující kód ukazuje, jak přidat nový záznam <xref:System.Data.DataTable> a následně zavolat `TableAdapter.Update` metody uložte nový řádek do databáze. (V tomto příkladu `Region` tabulky v databázi Northwind.)  
  
    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
   Pokud vaše aplikace používá k ukládání dat objektů, můžete použít `TableAdapter.Insert` metodu pro vytvoření nových řádků přímo v databázi. `Insert` Metoda přijímá jako parametry jednotlivé hodnoty pro každý sloupec. Volání metody vloží nový záznam do databáze se parametr hodnoty předané v.  
  
   Následující postup používá `Region` tabulky v databázi Northwind jako příklad.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Chcete-li vkládání nových záznamů do databáze s použitím TableAdapter.Insert – metoda  
  
-   Volání objektu TableAdapter `Insert` metodu předáním hodnoty pro každý sloupec jako parametry.  
  
    > [!NOTE]
    >  Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, které chcete použít.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Vkládání nových záznamů pomocí příkazu objektů  
 V následujícím příkladu vloží nové záznamy přímo do databáze pomocí příkazu objekty. Další informace o používání objektů příkazu ke spuštění příkazů a uložených procedur, naleznete v tématu [načítání dat do aplikace](../data-tools/fetching-data-into-your-application.md).  
  
 Následující postup používá `Region` tabulky v databázi Northwind jako příklad.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Chcete-li vkládání nových záznamů do databáze pomocí příkazu objektů  
  
-   Vytvořte nový objekt příkazu a pak nastavte jeho `Connection`, `CommandType`, a `CommandText` vlastnosti.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Musíte mít přístup k databázi, kterou se pokoušíte připojit k, jakož i oprávnění k provedení operace vložení do požadovanou tabulku.  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

