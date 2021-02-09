---
title: Uložení dat z objektu do databáze
description: Uložení dat z objektu do databáze pomocí nástrojů datové sady v sadě Visual Studio. Přečtěte si, jak uložit nové záznamy, aktualizovat existující záznamy a odstranit existující záznamy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 52bd4f95160165ee67c0a35816d094238786bc38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866564"
---
# <a name="save-data-from-an-object-to-a-database"></a>Uložení dat z objektu do databáze

Data v objektech můžete uložit do databáze předáním hodnot z objektu do jedné z TableAdapter metod DBDirect (například `TableAdapter.Insert` ). Další informace najdete v tématu [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Chcete-li uložit data z kolekce objektů, smyčka kolekcí objektů (například smyčka for-Next) a odeslat hodnoty pro každý objekt do databáze pomocí jedné z `DBDirect` metod TableAdapter.

Ve výchozím nastavení `DBDirect` jsou metody vytvořeny na TableAdapter, které lze spustit přímo proti databázi. Tyto metody lze volat přímo a nevyžadují <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> objekty pro sjednocení změn, aby bylo možné odesílat aktualizace do databáze.

> [!NOTE]
> Při konfiguraci TableAdapter musí hlavní dotaz poskytnout dostatek informací, aby `DBDirect` bylo možné metody vytvořit. Pokud je například TableAdapter nakonfigurovaný na dotazování dat z tabulky, která nemá definovaný sloupec primárního klíče, negeneruje `DBDirect` metody.

|TableAdapter DBDirect – metoda|Description|
| - |-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožňuje předat hodnoty jednotlivých sloupců jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje existující záznamy v databázi. `Update`Metoda přijímá původní a nové hodnoty sloupce jako parametry metody. Původní hodnoty se používají k vyhledání původního záznamu a k aktualizaci tohoto záznamu se použijí nové hodnoty.<br /><br /> `TableAdapter.Update`Metoda je také použita pro sjednocení změn v datové sadě zpět do databáze převzetím,, <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> nebo polem <xref:System.Data.DataRow> s jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze na základě původních hodnot sloupců předaných jako parametry metody.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Uložení nových záznamů z objektu do databáze

- Vytvořte záznamy předáním hodnot do `TableAdapter.Insert` metody.

     Následující příklad vytvoří nový záznam zákazníka v `Customers` tabulce předáním hodnot v `currentCustomer` objektu `TableAdapter.Insert` metodě.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aktualizace existujících záznamů z objektu na databázi

- Upravte záznamy voláním `TableAdapter.Update` metody, předáním nových hodnot k aktualizaci záznamu a předáním původních hodnot k vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat `Update` metodě. Tento příklad používá vlastnosti s `orig` předponou pro uložení původních hodnot.

     Následující příklad aktualizuje existující záznam v `Customers` tabulce předáním nových a původní hodnoty v `Customer` objektu `TableAdapter.Update` metodě.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Odstranění existujících záznamů z databáze

- Odstraňte záznamy voláním `TableAdapter.Delete` metody a předáním původních hodnot k vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat `Delete` metodě. Tento příklad používá vlastnosti s `orig` předponou pro uložení původních hodnot.

     Následující příklad odstraní záznam z `Customers` tabulky předáním původních hodnot v `Customer` objektu `TableAdapter.Delete` metodě.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Zabezpečení .NET

Musíte mít oprávnění k provedení vybraných `INSERT` , `UPDATE` nebo `DELETE` v tabulce v databázi.

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
