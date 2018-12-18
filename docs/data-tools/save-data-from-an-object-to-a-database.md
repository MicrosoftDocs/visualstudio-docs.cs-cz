---
title: Uložení dat z objektu do databáze
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1203b3b129b42ca65b94cd7a4b9cebf108740f4
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750946"
---
# <a name="save-data-from-an-object-to-a-database"></a>Uložení dat z objektu do databáze

Předáním hodnoty z objektu do jednoho objektu TableAdapter dbdirect – metody můžete uložit data v objektech k databázi (například `TableAdapter.Insert`). Další informace najdete v tématu [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

K uložení dat z kolekce objektů, procházet kolekci objektů (například smyčku pro další) a odeslání hodnoty pro každý objekt do databáze pomocí jedné z objektu TableAdapter `DBDirect` metody.

Ve výchozím nastavení `DBDirect` metody jsou vytvořeny v objektu typu TableAdapter, který můžete spustit přímo proti databázi. Tyto metody lze volat přímo a nevyžadují <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> objekty sloučit změny k odeslání aktualizací do databáze.

> [!NOTE]
> Při konfiguraci objektu typu TableAdapter, hlavního dotazu musí poskytnout dostatek informací, `DBDirect` metody, který se má vytvořit. Například pokud objektu TableAdapter je konfigurován pro dotazování na data z tabulky, která nemá sloupec primárního klíče definované, se nevygeneruje žádný `DBDirect` metody.

|TableAdapter dbdirect – metody|Popis|
| - |-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožňuje vám a zajistěte tak předání hodnot jednotlivých sloupců jako parametry metod.|
|`TableAdapter.Update`|Aktualizace existujících záznamů v databázi. `Update` Metoda má sloupec původní a nové hodnoty jako parametry metod. Původní hodnoty se používají pro vyhledání záznamu původní a nové hodnoty se používají k aktualizaci záznamu.<br /><br /> `TableAdapter.Update` Metoda slouží také k synchronizaci změn v datové sadě zpět do databáze pomocí <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, nebo pole <xref:System.Data.DataRow>označují jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze založené na původní hodnoty ve sloupcích předané jako parametry metod.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Chcete-li uložit nové záznamy z objektu do databáze

-   Vytvořte záznamy předáním hodnoty tak, aby `TableAdapter.Insert` metody.

     Následující příklad vytvoří nový záznam zákazníka v `Customers` předáním hodnoty v tabulce `currentCustomer` objektu `TableAdapter.Insert` metoda.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Chcete-li aktualizovat existující záznamy z objektu do databáze

-   Upravit záznamy voláním `TableAdapter.Update` metody předáním v nových hodnotách aktualizovat záznam a předáním v původní hodnoty, které mají vyhledejte záznam.

    > [!NOTE]
    > Objekt je potřeba udržovat původní hodnoty. Chcete-li předat jim `Update` metody. Tento příklad používá vlastnosti `orig` předpona, která uložit původní hodnoty.

     Následující příklad aktualizuje existující záznam v `Customers` předáním nových a původních hodnot v tabulce `Customer` objektu `TableAdapter.Update` metoda.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Můžete z databáze odstranit existující záznamy

-   Odstranit záznamy voláním `TableAdapter.Delete` metoda a předáním původní hodnoty, které mají vyhledejte záznam.

    > [!NOTE]
    > Objekt je potřeba udržovat původní hodnoty. Chcete-li předat jim `Delete` metody. Tento příklad používá vlastnosti `orig` předpona, která uložit původní hodnoty.

     Následující příklad odstraní záznam z `Customers` předáním původní hodnoty v tabulce `Customer` objektu `TableAdapter.Delete` metoda.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Musíte mít oprávnění k provádění vybraného `INSERT`, `UPDATE`, nebo `DELETE` na tabulku v databázi.

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)