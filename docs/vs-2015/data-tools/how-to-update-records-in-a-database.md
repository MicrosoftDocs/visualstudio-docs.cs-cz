---
title: 'Postupy: aktualizace záznamů v databázi | Dokumentace Microsoftu'
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b62dc86425dcbebb225c66eecd51505f674e20ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949029"
---
# <a name="how-to-update-records-in-a-database"></a>Postupy: Aktualizace záznamů v databázi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít `TableAdapter.Update` metodu pro záznamy aktualizace (úpravy) v databázi. `TableAdapter.Update` Metoda poskytuje několik přetížení, která provádět různé operace v závislosti na parametrech v. Je důležité pochopit, výsledky volání tyto podpisy jinou metodu.  
  
> [!NOTE]
>  Pokud vaše aplikace nepoužívá objekty TableAdapter, pak můžete použít objekty příkazu k aktualizaci záznamů v databázi (například <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Další informace o aktualizace dat pomocí příkazu objekty najdete v článku "Aktualizace záznamů pomocí objektů příkazu" níže.  
  
 Následující tabulka popisuje chování různých `TableAdapter.Update` metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Se pokusí uložit všechny změny v <xref:System.Data.DataTable> do databáze. (To zahrnuje, odebírá všechny řádky odstraněné z tabulky, přidávání řádků vložen do tabulky a aktualizaci všech řádků v tabulce, které se změnily.)|  
|`TableAdapter.Update(DataSet)`|I když parametr datové sady přidružené k objektu TableAdapter pokusí uložit všechny změny v TableAdapter <xref:System.Data.DataTable> do databáze. (To zahrnuje, odebírá všechny řádky odstraněné z tabulky, přidávání vložit řádky v tabulce a aktualizaci všech řádků v tabulce, které se změnily.) **Poznámka:** přidružený k tomuto objektu TableAdapter <xref:System.Data.DataTable> je <xref:System.Data.DataTable> vytvořena při konfiguraci objektu TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Pokusí se uložit změny v označený <xref:System.Data.DataRow> do databáze.|  
|`TableAdapter.Update(DataRows())`|Pokusí se uložit změny do libovolného řádku v poli <xref:System.Data.DataRow>s do databáze.|  
|`TableAdapter.Update("new column values", "original column values")`|Pokusy o uložení změn v jediném řádku, který je identifikován podle původní hodnoty ve sloupcích.|  
  
 Obvykle se používá `TableAdapter.Update` metodu, která přebírá <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow>(s), když vaše aplikace používá výhradně k ukládání dat datové sady.  
  
 Obvykle se používá `TableAdapter.Update` metodu, která přebírá hodnot sloupce, když vaše aplikace používá k ukládání dat objektů.  
  
 Pokud vaše TableAdapter nemá `Update` metodu, která přebírá hodnot sloupců a pak to znamená, že buď objektu TableAdapter je nakonfigurován na použití uložené procedury nebo jeho `GenerateDBDirectMethods` je nastavena na `false`. Nastavte TableAdapter `GenerateDBDirectMethods` vlastnost `true` v rámci [Návrhář Dataset](../data-tools/creating-and-editing-typed-datasets.md) a uložte datovou sadu znovu vygenerovat TableAdapter. Pokud TableAdapter ještě nemá žádné `Update` metodu, která přebírá hodnoty ve sloupcích tabulky a pravděpodobně neposkytuje dostatek informací o schématu rozlišovat mezi jednotlivé řádky (například žádný primární klíč je nastavený v tabulce).  
  
## <a name="update-existing-records-using-tableadapters"></a>Aktualizovat existující záznamy pomocí objektů TableAdapter  
 Objekty TableAdapter umožňují různé způsoby, jak aktualizovat záznamy v databázi v závislosti na požadavcích vaší aplikace.  
  
 Pokud vaše aplikace používá k ukládání dat datové sady, pak můžete jednoduše aktualizovat záznamy v požadovaný <xref:System.Data.DataTable> a následně zavolat `TableAdapter.Update` a předáte buď <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, nebo pole <xref:System.Data.DataRow>s. Výše uvedené tabulce popisuje různé `Update` metody.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>K aktualizaci záznamů v databázi, která přijímá datovou sadu, DataTable, DataRow nebo DataRows() TableAdapter.Update – metoda  
  
1. Úprava záznamů v požadovaný <xref:System.Data.DataTable> přímou úpravou <xref:System.Data.DataRow> v <xref:System.Data.DataTable>. Další informace najdete v tématu [postupy: úprava řádků z DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2. Po úpravě řádky v <xref:System.Data.DataTable>, zavolejte `TableAdapter.Update` metoda. Můžete řídit objem dat se aktualizovat předáním buď celý <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, pole <xref:System.Data.DataRow>s nebo jediný <xref:System.Data.DataRow>.  
  
    Následující kód ukazuje, jak upravit záznam v <xref:System.Data.DataTable> a následně zavolat `TableAdapter.Update` metoda a uložte změny do databáze. (Tento příklad používá oblasti tabulky databáze Northwind.)  
  
    [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
    [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
   Pokud vaše aplikace používá objekty k uložení dat v aplikaci, můžete použít objektu TableAdapter `DBDirect` metody k odeslání dat z objektů přímo do databáze. Tyto metody umožňují předat jako parametry metody jednotlivé hodnoty pro každý sloupec. Voláním této metody aktualizuje existující záznam v databázi s sloupec hodnoty předané do metody.  
  
   Následující postup používá Northwind `Region` tabulku s ukázkovým.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>K aktualizaci záznamů v databázi pomocí TableAdapter.Update – metoda, která přebírá hodnoty sloupců  
  
-   Volání objektu TableAdapter `Update` předejte jako původní a nové hodnoty pro každý sloupec jako parametry.  
  
    > [!NOTE]
    >  Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, které chcete použít.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Aktualizace záznamů pomocí příkazu objekty  
 Následující příklad aktualizují existující záznamy přímo v databázi pomocí objektů příkazu. Další informace o používání objektů příkazu ke spuštění příkazů a uložených procedur, naleznete v tématu [načítání dat do aplikace](../data-tools/fetching-data-into-your-application.md).  
  
 Následující postup používá Northwind `Region` tabulku s ukázkovým.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Aktualizace existujících záznamů v databázi pomocí objektů příkazu  
  
-   Vytvořit nový objekt příkazu; Nastavte jeho `Connection`, `CommandType`, a `CommandText` vlastnosti; a pak otevřete připojení a spusťte příkaz.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Musíte mít přístup k databázi, kterou se pokoušíte připojit k, jakož i oprávnění k aktualizaci záznamů ve požadovanou tabulku.  
  
## <a name="see-also"></a>Viz také  
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Postupy: odstranění záznamů v databázi](../data-tools/how-to-delete-records-in-a-database.md)   
 [Vkládání nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md)   
 [Uložení dat z objektu do databáze](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Přehled datových aplikacích v sadě Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)