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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5208b7764949f6ba6d3e862c7a2102608afb7e24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648216"
---
# <a name="save-data-from-an-object-to-a-database"></a>Uložení dat z objektu do databáze

Data v objektech můžete uložit do databáze předáním hodnot z objektu do jedné z TableAdapter metod DBDirect (například `TableAdapter.Insert`). Další informace najdete v tématu [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Chcete-li uložit data z kolekce objektů, smyčka kolekcí objektů (například smyčka for-Next) a odeslat hodnoty pro každý objekt do databáze pomocí jedné z `DBDirect` metod TableAdapter.

Ve výchozím nastavení jsou `DBDirect` metody vytvořeny na TableAdapter, které lze spustit přímo proti databázi. Tyto metody lze volat přímo a nevyžadují <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> objekty pro sjednocení změn, aby bylo možné odesílat aktualizace do databáze.

> [!NOTE]
> Při konfiguraci TableAdapter musí hlavní dotaz poskytnout dostatek informací, aby bylo možné vytvořit metody `DBDirect`. Pokud je například TableAdapter nakonfigurovaný na dotazování dat z tabulky, která nemá definovaný sloupec primárního klíče, negeneruje metody `DBDirect`.

|TableAdapter DBDirect – metoda|Popis|
| - |-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožňuje předat hodnoty jednotlivých sloupců jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje existující záznamy v databázi. Metoda `Update` přebírá původní a nové hodnoty sloupce jako parametry metody. Původní hodnoty se používají k vyhledání původního záznamu a k aktualizaci tohoto záznamu se použijí nové hodnoty.<br /><br /> Metoda `TableAdapter.Update` slouží také k sjednocení změn v datové sadě zpět do databáze tím, že převezmete <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> nebo pole <xref:System.Data.DataRow>s jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze na základě původních hodnot sloupců předaných jako parametry metody.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Uložení nových záznamů z objektu do databáze

- Vytvořte záznamy předáním hodnot do metody `TableAdapter.Insert`.

     Následující příklad vytvoří nový záznam zákazníka v tabulce `Customers` tím, že předáte hodnoty v objektu `currentCustomer` do metody `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aktualizace existujících záznamů z objektu na databázi

- Upravte záznamy tak, že zavoláte metodu `TableAdapter.Update`, předáte nové hodnoty k aktualizaci záznamu a předáte do nich původní hodnoty pro vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat metodě `Update`. Tento příklad používá vlastnosti s předponou `orig` k uložení původních hodnot.

     Následující příklad aktualizuje existující záznam v tabulce `Customers` tím, že předáte nové a původní hodnoty v objektu `Customer` do metody `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Odstranění existujících záznamů z databáze

- Odstraňte záznamy voláním metody `TableAdapter.Delete` a předáním původních hodnot k vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat metodě `Delete`. Tento příklad používá vlastnosti s předponou `orig` k uložení původních hodnot.

     Následující příklad odstraní záznam z `Customers` tabulky předáním původních hodnot v objektu `Customer` do metody `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Zabezpečení .NET

Musíte mít oprávnění k provedení vybraných `INSERT`, `UPDATE` nebo `DELETE` v tabulce v databázi.

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)