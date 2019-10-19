---
title: Uložení dat z objektu do databáze | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607460"
---
# <a name="save-data-from-an-object-to-a-database"></a>Uložení dat z objektu do databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data v objektech můžete uložit do databáze předáním hodnot z objektu do jedné z TableAdapter metod DBDirect (například `TableAdapter.Insert`).

 Chcete-li uložit data z kolekce objektů, smyčka kolekcí objektů (například smyčka for-Next) a odeslat hodnoty pro každý objekt do databáze pomocí jedné z metod DBDirect TableAdapter.

 Ve výchozím nastavení jsou metody DBDirect vytvořeny na TableAdapter, které lze spustit přímo proti databázi. Tyto metody lze volat přímo a nevyžadují <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> objekty pro sjednocení změn, aby bylo možné odesílat aktualizace do databáze.

> [!NOTE]
> Při konfiguraci TableAdapter musí hlavní dotaz poskytnout dostatek informací, aby bylo možné vytvořit metody DBDirect. Pokud je například TableAdapter nakonfigurovaný na dotazování dat z tabulky, která nemá definovaný sloupec primárního klíče, negeneruje DBDirect metody.

|TableAdapter DBDirect – metoda|Popis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožňuje předat hodnoty jednotlivých sloupců jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje existující záznamy v databázi. Metoda `Update` přebírá původní a nové hodnoty sloupce jako parametry metody. Původní hodnoty se používají k vyhledání původního záznamu a k aktualizaci tohoto záznamu se použijí nové hodnoty.<br /><br /> Metoda `TableAdapter.Update` slouží také k sjednocení změn v datové sadě zpět do databáze tím, že převezmete <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> nebo pole <xref:System.Data.DataRow>s jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze na základě původních hodnot sloupců předaných jako parametry metody.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Uložení nových záznamů z objektu do databáze

- Vytvořte záznamy předáním hodnot do metody `TableAdapter.Insert`.

     Následující příklad vytvoří nový záznam zákazníka v tabulce `Customers` tím, že předáte hodnoty v objektu `currentCustomer` do metody `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aktualizace existujících záznamů z objektu na databázi

- Upravte záznamy tak, že zavoláte metodu `TableAdapter.Update`, předáte nové hodnoty k aktualizaci záznamu a předáte do nich původní hodnoty pro vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat metodě `Update`. Tento příklad používá vlastnosti s předponou `orig` k uložení původních hodnot.

     Následující příklad aktualizuje existující záznam v tabulce `Customers` tím, že předáte nové a původní hodnoty v objektu `Customer` do metody `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Odstranění existujících záznamů z databáze

- Odstraňte záznamy voláním metody `TableAdapter.Delete` a předáním původních hodnot k vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat metodě `Delete`. Tento příklad používá vlastnosti s předponou `orig` k uložení původních hodnot.

     Následující příklad odstraní záznam z `Customers` tabulky předáním původních hodnot v objektu `Customer` do metody `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Musíte mít oprávnění k provedení vybraných vložení, aktualizace nebo odstranění v tabulce v databázi.

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
