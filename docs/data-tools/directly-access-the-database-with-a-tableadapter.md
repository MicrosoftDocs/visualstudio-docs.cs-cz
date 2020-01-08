---
title: Přímý přístup k databázi pomocí objektu TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8fe408c090dbdc2157cd52977d4bbed66cfe9109
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586689"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Přímý přístup k databázi pomocí objektu TableAdapter

Kromě `InsertCommand`, `UpdateCommand`a `DeleteCommand`jsou vytvořeny objekty TableAdapter s metodami, které lze spustit přímo proti databázi. Můžete zavolat tyto metody (`TableAdapter.Insert`, `TableAdapter.Update`a `TableAdapter.Delete`) k manipulaci s daty přímo v databázi.

Pokud nechcete vytvořit tyto přímé metody, nastavte vlastnost `GenerateDbDirectMethods` TableAdapter na `false` v okně **vlastnosti** . Pokud jsou do TableAdapter přidané nějaké dotazy kromě hlavního dotazu TableAdapter, jedná se o samostatné dotazy, které tyto metody negenerují `DbDirect`.

## <a name="send-commands-directly-to-a-database"></a>Posílání příkazů přímo do databáze

Zavolejte TableAdapter `DbDirect` metodu, která provede úkol, který se pokoušíte provést.

### <a name="to-insert-new-records-directly-into-a-database"></a>Vložení nových záznamů přímo do databáze

- Zavolejte metodu `Insert` TableAdapter a předejte hodnoty pro každý sloupec jako parametry. Následující postup používá jako příklad tabulku `Region` v databázi Northwind.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Postup aktualizace záznamů přímo v databázi

- Zavolejte metodu `Update` TableAdapter a předejte nové a původní hodnoty pro každý sloupec jako parametry.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Postup odstranění záznamů přímo z databáze

- Zavolejte metodu `Delete` TableAdapter a předejte hodnoty pro každý sloupec jako parametry metody `Delete`. Následující postup používá jako příklad tabulku `Region` v databázi Northwind.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Viz také:

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
