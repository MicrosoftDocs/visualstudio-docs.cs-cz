---
title: Aktualizace dat pomocí objektu TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b54aeb91ea873b23b1e68731e40542df04fcbd01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648116"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizace dat pomocí objektu TableAdapter

Po úpravě a ověření dat ve vaší datové sadě můžete aktualizovaná data odeslat zpět do databáze voláním metody `Update` [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Metoda `Update` aktualizuje jedinou datovou tabulku a spustí správný příkaz (INSERT, UPDATE nebo DELETE) na základě <xref:System.Data.DataRow.RowState%2A> každého řádku dat v tabulce. Pokud má datová sada související tabulky, aplikace Visual Studio vygeneruje třídu TableAdapterManager, kterou použijete k provedení aktualizací. Třída TableAdapterManager zajišťuje, že aktualizace budou provedeny ve správném pořadí na základě omezení cizího klíče, které jsou definovány v databázi. Při použití ovládacích prvků vázaných na data vytvoří architektura datové vazby členskou proměnnou třídy TableAdapterManager s názvem tableAdapterManager.

> [!NOTE]
> Když se pokusíte aktualizovat zdroj dat obsahem datové sady, můžete získat chyby. Aby se předešlo chybám, doporučujeme, abyste vložili kód, který do `try` / `catch` bloku zavolá metodu `Update` adaptéru.

Přesný postup pro aktualizaci zdroje dat se může lišit v závislosti na obchodních potřebách, ale obsahuje následující kroky:

1. Zavolejte `Update`ovou metodu adaptéru ve `try` / bloku `catch`.

2. Pokud je zachycena výjimka, vyhledejte řádek dat, který způsobil chybu.

3. Odsouhlasení problému na řádku dat (pokud můžete, nebo zadáním neplatného řádku pro úpravu), a potom zkuste aktualizaci zopakovat (<xref:System.Data.DataRow.HasErrors%2A> <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Uložení dat do databáze

Zavolejte metodu `Update` TableAdapter. Předejte název tabulky dat obsahující hodnoty, které mají být zapsány do databáze.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aktualizace databáze pomocí TableAdapter

- Uzavřete `Update` metodu TableAdapter do `try` / bloku `catch`. Následující příklad ukazuje, jak aktualizovat obsah `Customers` tabulky v `NorthwindDataSet` v rámci `try` / `catch` bloku.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)