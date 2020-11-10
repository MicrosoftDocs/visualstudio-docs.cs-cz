---
title: Přímý přístup k databázi pomocí objektu TableAdapter
description: Přímý přístup k databázi pomocí TableAdapter pomocí metod, jako je vložení, aktualizace a odstranění, pro manipulaci s daty přímo v databázi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ebf6233116c62ee1e25e2bef0ab4d80bdec029b7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435179"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Přímý přístup k databázi pomocí objektu TableAdapter

Kromě rozhraní `InsertCommand` , `UpdateCommand` a `DeleteCommand` objekty TableAdapter jsou vytvořeny pomocí metod, které lze spustit přímo proti databázi. Můžete zavolat tyto metody ( `TableAdapter.Insert` , `TableAdapter.Update` a `TableAdapter.Delete` ) pro manipulaci s daty přímo v databázi.

Pokud nechcete vytvořit tyto přímé metody, nastavte `GenerateDbDirectMethods` vlastnost TableAdapter na hodnotu `false` v okně **vlastnosti** . Pokud jsou do TableAdapter přidané nějaké dotazy kromě hlavního dotazu TableAdapter, jedná se o samostatné dotazy, které tyto metody negenerují `DbDirect` .

## <a name="send-commands-directly-to-a-database"></a>Posílání příkazů přímo do databáze

Zavolejte metodu TableAdapter `DbDirect` , která provede úkol, který se pokoušíte provést.

### <a name="to-insert-new-records-directly-into-a-database"></a>Vložení nových záznamů přímo do databáze

- Zavolejte `Insert` metodu TableAdapter a předejte hodnoty pro každý sloupec jako parametry. Následující postup používá `Region` jako příklad tabulku v databázi Northwind.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Postup aktualizace záznamů přímo v databázi

- Zavolejte `Update` metodu TableAdapter a předejte nové a původní hodnoty pro každý sloupec jako parametry.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Postup odstranění záznamů přímo z databáze

- Zavolejte `Delete` metodu TableAdapter a předejte hodnoty pro každý sloupec jako parametry `Delete` metody. Následující postup používá `Region` jako příklad tabulku v databázi Northwind.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Viz také

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
