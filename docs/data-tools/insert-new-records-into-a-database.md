---
title: Vkládání nových záznamů do databáze
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae5ec2197ff2a899f27df20e7199fdeb7a02d31
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949198"
---
# <a name="insert-new-records-into-a-database"></a>Vkládání nových záznamů do databáze

Vkládání nových záznamů do databáze, můžete `TableAdapter.Update` metody nebo jeden z objektu TableAdapter dbdirect – metody (konkrétně `TableAdapter.Insert` metoda). Další informace najdete v tématu [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Pokud vaše aplikace nepoužívá objekty TableAdapter, můžete použít příkaz objektů (například <xref:System.Data.SqlClient.SqlCommand>) pro vkládání nových záznamů do databáze.

Pokud vaše aplikace používá k ukládání dat datové sady, použijte `TableAdapter.Update` metody. `Update` Metoda odešle všechny změny (aktualizací, vložení a odstranění) do databáze.

Pokud vaše aplikace používá objekty k ukládání dat, nebo pokud chcete lepší kontrolu nad vytváření nových záznamů v databázi, použijte `TableAdapter.Insert` metody.

Pokud vaše TableAdapter nemá `Insert` metoda, znamená to, že buď objektu TableAdapter je nakonfigurován na použití uložené procedury nebo jeho `GenerateDBDirectMethods` je nastavena na `false`. Nastavte TableAdapter `GenerateDBDirectMethods` vlastnost `true` v rámci **Návrhář Dataset**a potom uložte datovou sadu. Tímto se znova vygeneruje TableAdapter. Pokud TableAdapter stále nemá `Insert` metody tabulce pravděpodobně neposkytuje dostatek informací o schématu rozlišovat mezi jednotlivé řádky (například může existovat žádná sada je primární klíče v tabulce).

## <a name="insert-new-records-by-using-tableadapters"></a>Vkládání nových záznamů pomocí objektů TableAdapter

Objekty TableAdapter umožňují různé způsoby vkládání nových záznamů do databáze, v závislosti na požadavcích vaší aplikace.

Pokud vaše aplikace používá k ukládání dat datové sady, můžete jednoduše přidat nové záznamy na požadovaný <xref:System.Data.DataTable> datovou sadu, a poté zavolejte `TableAdapter.Update` metody. `TableAdapter.Update` Metoda odešle všechny změny v <xref:System.Data.DataTable> k databázi (včetně upravené a odstraněné záznamy).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Chcete-li vkládání nových záznamů do databáze s použitím TableAdapter.Update – metoda

1. Přidání nových záznamů do požadované <xref:System.Data.DataTable> vytvořením nového <xref:System.Data.DataRow> a jejím přidáním na <xref:System.Data.DataTable.Rows%2A> kolekce.

2. Po přidání nových řádků do <xref:System.Data.DataTable>, zavolejte `TableAdapter.Update` metody. Můžete řídit objem dat se aktualizovat předáním buď celý <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, pole <xref:System.Data.DataRow>s nebo jediný <xref:System.Data.DataRow>.

   Následující kód ukazuje, jak přidat nový záznam <xref:System.Data.DataTable> a následně zavolat `TableAdapter.Update` metody uložte nový řádek do databáze. (V tomto příkladu `Region` tabulky v databázi Northwind.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Chcete-li vkládání nových záznamů do databáze s použitím TableAdapter.Insert – metoda

Pokud vaše aplikace používá k ukládání dat objektů, můžete použít `TableAdapter.Insert` metodu pro vytvoření nových řádků přímo v databázi. `Insert` Metoda přijímá jako parametry jednotlivé hodnoty pro každý sloupec. Volání metody vloží nový záznam do databáze se parametr hodnoty předané v.

- Volání objektu TableAdapter `Insert` metodu předáním hodnoty pro každý sloupec jako parametry.

Následující postup ukazuje, jak pomocí `TableAdapter.Insert` metodu pro vkládání řádků. V tomto příkladu vloží data do `Region` tabulky v databázi Northwind.

> [!NOTE]
> Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, které chcete použít.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Vkládání nových záznamů pomocí příkazu objektů

Vkládání nových záznamů přímo do databáze pomocí příkazu objektů.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Chcete-li vkládání nových záznamů do databáze pomocí příkazu objektů

- Vytvořte nový objekt příkazu a pak nastavte jeho `Connection`, `CommandType`, a `CommandText` vlastnosti.

Následující příklad ukazuje vkládání záznamů do databáze pomocí objektu příkazu. Vkládá data do `Region` tabulky v databázi Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Musíte mít přístup k databázi, kterou se pokoušíte připojit k, jakož i oprávnění k provedení operace vložení do požadovanou tabulku.

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)