---
title: Vkládání nových záznamů do databáze
description: Vložte nové záznamy do databáze pomocí metody TableAdapter. Update, jedné z DBDirect metod TableAdapter nebo objektů příkazů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 6e1046dfd114e4cad69445b8f4e1432c03aac0e5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216459"
---
# <a name="insert-new-records-into-a-database"></a>Vkládání nových záznamů do databáze

Pro vložení nových záznamů do databáze můžete použít `TableAdapter.Update` metodu nebo jednu z metod DBDirect pro TableAdapter (konkrétně `TableAdapter.Insert` Metoda). Další informace najdete v tématu [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Pokud vaše aplikace nepoužívá objekty TableAdapter, můžete použít objekty příkazu (například  <xref:System.Data.SqlClient.SqlCommand> ) k vložení nových záznamů do databáze.

Pokud vaše aplikace používá k ukládání dat datové sady, použijte `TableAdapter.Update` metodu. `Update`Metoda odesílá do databáze všechny změny (aktualizace, vkládání a odstraňování).

Pokud vaše aplikace používá objekty k ukládání dat nebo pokud chcete lepší kontrolu nad vytvářením nových záznamů v databázi, použijte `TableAdapter.Insert` metodu.

Pokud vaše TableAdapter nemá `Insert` metodu, znamená to, že buď je TableAdapter nakonfigurovaná na použití uložených procedur, nebo `GenerateDBDirectMethods` je jeho vlastnost nastavena na `false` . Zkuste nastavit `GenerateDBDirectMethods` vlastnost TableAdapter na v `true` rámci **Návrhář datových sad** a pak datovou sadu uložte. Tím se znovu vygeneruje TableAdapter. Pokud TableAdapter stále nemá `Insert` metodu, tabulka pravděpodobně neposkytuje dostatek informací o schématu pro odlišení jednotlivých řádků (například v tabulce nemusí být nastaven žádný primární klíč).

## <a name="insert-new-records-by-using-tableadapters"></a>Vložení nových záznamů pomocí objekty TableAdapter

Objekty TableAdapter poskytují různé způsoby vkládání nových záznamů do databáze v závislosti na požadavcích vaší aplikace.

Pokud vaše aplikace používá k ukládání dat datové sady, můžete jednoduše přidat nové záznamy na požadované <xref:System.Data.DataTable> v datové sadě a pak zavolat `TableAdapter.Update` metodu. `TableAdapter.Update`Metoda odesílá všechny změny v <xref:System.Data.DataTable> databázi (včetně upravených a odstraněných záznamů).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Vložení nových záznamů do databáze pomocí metody TableAdapter. Update

1. Přidejte nové záznamy na požadované <xref:System.Data.DataTable> vytvořením nového <xref:System.Data.DataRow> a přidáním do <xref:System.Data.DataTable.Rows%2A> kolekce.

2. Po přidání nových řádků do do <xref:System.Data.DataTable> volejte `TableAdapter.Update` metodu. Množství dat, která se mají aktualizovat, můžete řídit předáním buď celého <xref:System.Data.DataSet> , a <xref:System.Data.DataTable> , pole <xref:System.Data.DataRow> s nebo jednoho <xref:System.Data.DataRow> .

   Následující kód ukazuje, jak přidat nový záznam do <xref:System.Data.DataTable> a pak zavolat `TableAdapter.Update` metodu pro uložení nového řádku do databáze. (V tomto příkladu se používá `Region` tabulka v databázi Northwind.)

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb" id="Snippet14":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs" id="Snippet14":::

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Vložení nových záznamů do databáze pomocí metody TableAdapter. Insert

Pokud vaše aplikace používá objekty k ukládání dat, můžete pomocí `TableAdapter.Insert` metody vytvořit nové řádky přímo v databázi. `Insert`Metoda přijímá jednotlivé hodnoty pro každý sloupec jako parametry. Volání metody vloží nový záznam do databáze s předanými hodnotami parametrů.

- Zavolejte `Insert` metodu TableAdapter a předejte hodnoty pro každý sloupec jako parametry.

Následující postup ukazuje použití `TableAdapter.Insert` metody pro vložení řádků. Tento příklad vloží data do `Region` tabulky v databázi Northwind.

> [!NOTE]
> Pokud nemáte k dispozici instanci, vytvořte instanci objektu TableAdapter, který chcete použít.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

## <a name="insert-new-records-by-using-command-objects"></a>Vložení nových záznamů pomocí objektů příkazů

Nové záznamy lze vkládat přímo do databáze pomocí objektů příkazů.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Vložení nových záznamů do databáze pomocí objektů příkazů

- Vytvořte nový objekt příkazu a pak nastavte jeho `Connection` vlastnosti, a `CommandType` `CommandText` .

Následující příklad ukazuje vložení záznamů do databáze pomocí objektu Command. Vloží data do `Region` tabulky v databázi Northwind.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet16":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet16":::

## <a name="net-security"></a>Zabezpečení .NET

Musíte mít přístup k databázi, ke které se pokoušíte připojit, a také oprávnění k provádění vložení do požadované tabulky.

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
