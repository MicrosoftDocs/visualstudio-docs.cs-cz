---
title: Vložení nových záznamů do databáze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651562"
---
# <a name="insert-new-records-into-a-database"></a>Vkládání nových záznamů do databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li vložit nové záznamy do databáze, můžete použít metodu `TableAdapter.Update` nebo jednu z DBDirect metod TableAdapter (konkrétně metoda `TableAdapter.Insert`).

 Pokud vaše aplikace nepoužívá objekty TableAdapter, můžete k vložení nových záznamů do databáze použít objekty příkazu (například <xref:System.Data.SqlClient.SqlCommand>).

 Pokud vaše aplikace používá k ukládání dat datové sady, použijte metodu `TableAdapter.Update`. Metoda `Update` odesílá všechny změny (aktualizace, vkládání a odstraňování) do databáze.

 Pokud vaše aplikace používá objekty k ukládání dat nebo pokud chcete lepší kontrolu nad vytvářením nových záznamů v databázi, použijte metodu `TableAdapter.Insert`.

 Pokud vaše TableAdapter nemá metodu `Insert`, znamená to, že TableAdapter je nakonfigurován tak, aby používal uložené procedury nebo vlastnost `GenerateDBDirectMethods` je nastavená na `false`. Zkuste nastavit vlastnost `GenerateDBDirectMethods` TableAdapter na `true` v rámci Návrhář datových sad a pak datovou sadu uložte. Tím se znovu vygeneruje TableAdapter. Pokud TableAdapter stále nemá metodu `Insert`, pak tabulka pravděpodobně neposkytuje dostatek informací o schématu pro odlišení jednotlivých řádků (například v tabulce nemusí být nastaven žádný primární klíč).

## <a name="insert-new-records-by-using-tableadapters"></a>Vložení nových záznamů pomocí objekty TableAdapter
 Objekty TableAdapter poskytují různé způsoby vkládání nových záznamů do databáze v závislosti na požadavcích vaší aplikace.

 Pokud vaše aplikace používá k ukládání dat datové sady, můžete jednoduše přidat nové záznamy do požadovaných <xref:System.Data.DataTable> v datové sadě a pak zavolat metodu `TableAdapter.Update`. Metoda `TableAdapter.Update` odesílá všechny změny v <xref:System.Data.DataTable> do databáze (včetně upravených a odstraněných záznamů).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Vložení nových záznamů do databáze pomocí metody TableAdapter. Update

1. Přidejte nové záznamy do požadovaných <xref:System.Data.DataTable> vytvořením nového <xref:System.Data.DataRow> a jeho přidáním do kolekce <xref:System.Data.DataTable.Rows%2A>. Další informace najdete v tématu [Postup: Přidání řádků do objektu DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Po přidání nových řádků do <xref:System.Data.DataTable> volejte metodu `TableAdapter.Update`. Množství dat, která se mají aktualizovat, můžete řídit předáním celého <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, pole <xref:System.Data.DataRow>s nebo jednoho <xref:System.Data.DataRow>.

    Následující kód ukazuje, jak přidat nový záznam do <xref:System.Data.DataTable> a pak zavolat metodu `TableAdapter.Update` k uložení nového řádku do databáze. (V tomto příkladu se používá tabulka `Region` v databázi Northwind.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Pokud vaše aplikace používá objekty k ukládání dat, můžete pomocí metody `TableAdapter.Insert` vytvořit nové řádky přímo v databázi. Metoda `Insert` přijímá jednotlivé hodnoty pro každý sloupec jako parametry. Volání metody vloží nový záznam do databáze s předanými hodnotami parametrů.

   Následující postup používá jako příklad tabulku `Region` v databázi Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Vložení nových záznamů do databáze pomocí metody TableAdapter. Insert

- Zavolejte metodu `Insert` TableAdapter a předejte hodnoty pro každý sloupec jako parametry.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci objektu TableAdapter, který chcete použít.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Vložení nových záznamů pomocí objektů příkazů
 Následující příklad vkládá nové záznamy přímo do databáze pomocí objektů příkazů.

 Následující postup používá jako příklad tabulku `Region` v databázi Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Vložení nových záznamů do databáze pomocí objektů příkazů

- Vytvořte nový objekt příkazu a nastavte jeho vlastnosti `Connection`, `CommandType` a `CommandText`.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Musíte mít přístup k databázi, ke které se pokoušíte připojit, a také oprávnění k provádění vložení do požadované tabulky.

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
