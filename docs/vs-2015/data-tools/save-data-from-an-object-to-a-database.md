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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607460"
---
# <a name="save-data-from-an-object-to-a-database"></a>Uložení dat z objektu do databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data v objektech můžete uložit do databáze předáním hodnot z objektu do jedné z TableAdapter metod DBDirect (například `TableAdapter.Insert` ).

 Chcete-li uložit data z kolekce objektů, smyčka kolekcí objektů (například smyčka for-Next) a odeslat hodnoty pro každý objekt do databáze pomocí jedné z metod DBDirect TableAdapter.

 Ve výchozím nastavení jsou metody DBDirect vytvořeny na TableAdapter, které lze spustit přímo proti databázi. Tyto metody lze volat přímo a nevyžadují <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> objekty pro sjednocení změn, aby bylo možné odesílat aktualizace do databáze.

> [!NOTE]
> Při konfiguraci TableAdapter musí hlavní dotaz poskytnout dostatek informací, aby bylo možné vytvořit metody DBDirect. Pokud je například TableAdapter nakonfigurovaný na dotazování dat z tabulky, která nemá definovaný sloupec primárního klíče, negeneruje DBDirect metody.

|TableAdapter DBDirect – metoda|Popis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožňuje předat hodnoty jednotlivých sloupců jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje existující záznamy v databázi. `Update`Metoda přijímá původní a nové hodnoty sloupce jako parametry metody. Původní hodnoty se používají k vyhledání původního záznamu a k aktualizaci tohoto záznamu se použijí nové hodnoty.<br /><br /> `TableAdapter.Update`Metoda je také použita pro sjednocení změn v datové sadě zpět do databáze převzetím,, <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> nebo polem <xref:System.Data.DataRow> s jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze na základě původních hodnot sloupců předaných jako parametry metody.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Uložení nových záznamů z objektu do databáze

- Vytvořte záznamy předáním hodnot do `TableAdapter.Insert` metody.

     Následující příklad vytvoří nový záznam zákazníka v `Customers` tabulce předáním hodnot v `currentCustomer` objektu `TableAdapter.Insert` metodě.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aktualizace existujících záznamů z objektu na databázi

- Upravte záznamy voláním `TableAdapter.Update` metody, předáním nových hodnot k aktualizaci záznamu a předáním původních hodnot k vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat `Update` metodě. Tento příklad používá vlastnosti s `orig` předponou pro uložení původních hodnot.

     Následující příklad aktualizuje existující záznam v `Customers` tabulce předáním nových a původní hodnoty v `Customer` objektu `TableAdapter.Update` metodě.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Odstranění existujících záznamů z databáze

- Odstraňte záznamy voláním `TableAdapter.Delete` metody a předáním původních hodnot k vyhledání záznamu.

    > [!NOTE]
    > Váš objekt musí zachovat původní hodnoty, aby je bylo možné předat `Delete` metodě. Tento příklad používá vlastnosti s `orig` předponou pro uložení původních hodnot.

     Následující příklad odstraní záznam z `Customers` tabulky předáním původních hodnot v `Customer` objektu `TableAdapter.Delete` metodě.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Musíte mít oprávnění k provedení vybraných vložení, aktualizace nebo odstranění v tabulce v databázi.

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
