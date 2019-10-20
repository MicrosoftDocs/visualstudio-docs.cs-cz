---
title: Přímý přístup k databázi pomocí TableAdapter | Microsoft Docs
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657365"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Přímý přístup k databázi pomocí objektu TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kromě `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou vytvořeny objekty TableAdapter s metodami, které lze spustit přímo proti databázi. Tyto metody (`TableAdapter.Insert`, `TableAdapter.Update` a `TableAdapter.Delete`) lze volat pro manipulaci s daty přímo v databázi.

 Pokud nechcete vytvořit tyto přímé metody, nastavte vlastnost `GenerateDbDirectMethods` TableAdapter na `false` v okně **vlastnosti** . Pokud jsou do TableAdapter přidané nějaké dotazy kromě hlavního dotazu TableAdapter, jedná se o samostatné dotazy, které tyto metody DbDirect negenerují.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly k databázi
 Zavolejte metodu TableAdapter DbDirect, která provede úkol, který se pokoušíte provést.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Vložení nových záznamů přímo do databáze

- Zavolejte metodu `Insert` TableAdapter a předejte hodnoty pro každý sloupec jako parametry. Následující postup používá v databaseas příkladu tabulku `Region`.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Postup aktualizace záznamů přímo v databázi

- Zavolejte metodu `Update` TableAdapter a předejte nové a původní hodnoty pro každý sloupec jako parametry.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Postup odstranění záznamů přímo z databáze

- Zavolejte metodu `Delete` TableAdapter a předejte hodnoty pro každý sloupec jako parametry metody `Delete`. Následující postup používá v databaseas příkladu tabulku `Region`.

    > [!NOTE]
    > Pokud nemáte k dispozici instanci, vytvořte instanci TableAdapter, kterou chcete použít.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Viz také
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
