---
title: 'Postupy: uložení změn datové sady do databáze | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 60bb855202cfb333820fe2292fedc0b31608c5c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949016"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Postupy: Uložení změn datové sady do databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po dat ve vaší datové sadě byl změněn a ověřit, budete pravděpodobně chtít odeslat aktualizovaná data zpět do databáze. Aby bylo možné odesílat upravených dat do databáze, volání `Update` metodu [TableAdapter](../data-tools/tableadapter-overview.md) nebo datový adaptér. Adaptéru `Update` metodu aktualizace jedné tabulky datového a provede příkaz správné (vložení, aktualizace nebo odstranění) na základě <xref:System.Data.DataRow.RowState%2A> každého řádku dat v tabulce.  
  
 Při ukládání dat v souvisejících tabulkách, poskytuje Visual Studio vytvářet komponentu TableAdapterManager, který pomáhá při provádění uloží ve správném pořadí podle omezení cizího klíče definovanými v databázi. Další informace najdete v tématu [přehled hierarchické aktualizace](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Protože pokus o aktualizaci zdroje dat s obsahem datové sady, může mít za následek chyby, měli byste umístit kód, který volá adaptéru `Update` metoda uvnitř `try` / `catch` bloku.  
  
 Přesný postup k aktualizaci zdroje dat se může lišit v závislosti na vašich obchodních potřeb, ale vaše aplikace by měl obsahovat následující kroky:  
  
1.  Spustit kód, který se pokusí odesláním aktualizací k databázi v rámci `try` / `catch` bloku.  
  
2.  Pokud je výjimka zachycena, vyhledejte řádek dat, která způsobila chybu. Další informace najdete v tématu [postupy: vyhledání řádků chyby mají](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Sjednotit problém v datech řádku (prostřednictvím kódu programu, pokud je to možné, nebo tím, že předloží neplatný řádek pro uživatele pro úpravy) a pak zkuste znovu provést aktualizaci (<xref:System.Data.DataRow.HasErrors%2A> vlastnost <xref:System.Data.DataTable.GetErrors%2A> metoda).  
  
## <a name="saving-data-to-a-database"></a>Ukládání dat do databáze  
 Volání `Update` metoda TableAdapter nebo datového adaptéru, předejte název tabulky dat, který obsahuje hodnoty, které mají být zapsána do databáze. Další informace o ukládání dat z jedné tabulky datového zpět do databáze, najdete v části [návod: ukládání dat do databáze (jediná tabulka)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Aktualizace databáze s datovou sadou pomocí prvku TableAdapter  
  
-   Uzavřete `TableAdapter.Update` metodu `try` / `catch` bloku. Následující příklad ukazuje, jak aktualizovat s obsahem `Customers` v tabulku `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Aktualizace databáze s datovou sadou pomocí adaptéru dat  
  
-   Uzavřete `DataAdapter.Update` metodu `try` / `catch` bloku. Následující příklad ukazuje, jak aktualizovat ke zdroji dat s obsahem `Table1` v `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>Aktualizuje se dvou souvisejících tabulek v datové sadě  
 Při aktualizaci souvisejících tabulkách v datové sadě, je potřeba aktualizovat ve správném pořadí, abyste snížili riziko porušení omezení referenční integrity. Pořadí provádění příkazu bude následovat také indexy <xref:System.Data.DataRowCollection> v datové sadě. Abyste zabránili vyvolaných chyby integrity dat, osvědčeným postupem je aktualizovat databázi v následujícím pořadí:  
  
1. Podřízené tabulky: odstranění záznamů.  
  
2. Nadřazená tabulka: vložit, aktualizovat a odstraňovat záznamy.  
  
3. Podřízené tabulky: vkládací a aktualizační záznamy.  
  
   Podrobné informace o ukládání dat z více tabulek, naleznete v tématu [ukládání dat do databáze (více tabulek)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
   Pokud provádíte aktualizaci dvou nebo více souvisejících tabulek, měli byste zahrnout veškerou logiku aktualizací v rámci transakce. Transakce je proces, který zajišťuje všechny související změny do databáze se úspěšně před potvrzením změny. Další informace najdete v tématu [transakce a souběžnost](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Chcete-li aktualizovat dvou souvisejících tabulek pomocí prvku TableAdapter  
  
1.  Vytvořte tři dočasné <xref:System.Data.DataTable>s obsahují různé záznamy.  
  
2.  Volání `Update` metoda pro každou podmnožinu řádků v rámci `try` / `catch` bloku. Pokud dojde k chybě aktualizace, je doporučený postup větví a jejich řešení.  
  
3.  Potvrďte změny z datové sady do databáze.  
  
4.  Odstranění tabulky dočasná data a uvolnit tak prostředky.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Chcete-li aktualizovat dvou souvisejících tabulek pomocí adaptéru dat  
  
-   Volání `Update` metoda každý datový adaptér.  
  
     Následující příklad ukazuje, jak aktualizovat zdroj dat s datovou sadou, který obsahuje související tabulky. Pokud chcete postupovat podle výše uvedené pořadí tří dočasné <xref:System.Data.DataTable>s se vytvoří pro uložení různý záznamy. Pak bude `Update` metoda bude zavolána pro každou podmnožinu řádků v rámci `try` / `catch` bloku. Pokud dojde k chybě aktualizace, je doporučený postup větví a jejich řešení. Potom datovou sadu potvrzení změn. A konečně odstranění tabulky dočasná data a uvolnit tak prostředky.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)