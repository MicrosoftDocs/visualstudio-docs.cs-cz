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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 22a2580809394ba1b41e7923f4f2df458d995a93
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750959"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Přímý přístup k databázi pomocí objektu TableAdapter

Kromě `InsertCommand`, `UpdateCommand`, a `DeleteCommand`, jsou objekty TableAdapter vytvořeny metodami, které lze spustit přímo proti databázi. Můžete volat tyto metody (`TableAdapter.Insert`, `TableAdapter.Update`, a `TableAdapter.Delete`) pro manipulaci s daty přímo v databázi.

Pokud tyto přímé metody vytvořit nechcete, nastavte TableAdapter `GenerateDbDirectMethods` vlastnost `false` v **vlastnosti** okna. Pokud přidáte všechny dotazy objektu TableAdapter kromě hlavním dotazem objektu TableAdapter jsou samostatné dotazy, které tyto negenerovat `DbDirect` metody.

## <a name="send-commands-directly-to-a-database"></a>Odesílat příkazy přímo k databázi

Volání objektu TableAdapter `DbDirect` metodu, která provádí úlohy se pokoušíte provést.

### <a name="to-insert-new-records-directly-into-a-database"></a>Chcete-li vkládání nových záznamů přímo do databáze

-   Volání objektu TableAdapter `Insert` metodu předáním hodnoty pro každý sloupec jako parametry. Následující postup používá `Region` tabulky v databázi Northwind jako příklad.

    > [!NOTE]
    > Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, který chcete použít.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>K aktualizaci záznamů přímo do databáze

-   Volání objektu TableAdapter `Update` předejte jako původní a nové hodnoty pro každý sloupec jako parametry.

    > [!NOTE]
    > Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, který chcete použít.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Můžete přímo z databáze odstranit záznamy

-   Volání objektu TableAdapter `Delete` metodu předáním hodnoty pro každý sloupec jako parametry `Delete` metody. Následující postup používá `Region` tabulky v databázi Northwind jako příklad.

    > [!NOTE]
    > Pokud nemáte k dispozici instance, vytvořte instanci objektu TableAdapter, který chcete použít.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Viz také:

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)