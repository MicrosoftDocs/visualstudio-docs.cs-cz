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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 88d4da868174396bfed148fc6088e5675e1198b2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116890"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizace dat pomocí objektu TableAdapter

Poté, co byla upravena a ověřit data v datovou sadu, můžete odeslat aktualizovaná data zpět na databázi zavoláním `Update` metodu [TableAdapter](../data-tools/create-and-configure-tableadapters.md). `Update` Metoda aktualizace do jedné tabulky datového a spustí příkaz správný (INSERT, UPDATE nebo DELETE) na základě <xref:System.Data.DataRow.RowState%2A> z každý řádek dat v tabulce. Když datovou sadu s související tabulky, Visual Studio generuje TableAdapterManager třídy, které můžete použít k provedení aktualizace. Třída TableAdapterManager zajistí, že jsou ve správném pořadí podle omezení cizího klíče, které jsou definovány v databázi provedeny aktualizace. Pokud používáte ovládací prvky vázané na data, vytvoří architektuře vazby dat členské proměnné volané tableAdapterManager TableAdapterManager třídy.

> [!NOTE]
> Při pokusu aktualizovat zdroj dat s obsahem datovou sadu, může docházet k chybám. Abyste se vyhnuli chybám, doporučujeme vložit kód, který volá adaptéru `Update` metodu `try` / `catch` bloku.

 Přesný postup aktualizace zdroje dat se může lišit v závislosti na obchodních potřeb, ale zahrnuje následující kroky:

1.  Volání adaptéru `Update` metoda v `try` / `catch` bloku.

2.  Pokud je výjimka zachycena, vyhledejte řádek dat, která způsobila chybu.

3.  Odsouhlasení problém v datech řádku (prostřednictvím kódu programu, pokud je to možné, nebo prezentací neplatný řádek pro uživatele pro úpravy) a potom opakujte aktualizaci (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Uložení dat do databáze

Volání `Update` metoda TableAdapter. Předejte název tabulky dat, která obsahuje hodnoty, které mají být zapsána do databáze.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Chcete-li aktualizovat databázi pomocí TableAdapter

-   Uzavřete TableAdapter`Update` metoda v `try` / `catch` bloku. Následující příklad ukazuje, jak aktualizovat obsah `Customers` tabulky v `NorthwindDataSet` uvnitř `try` / `catch` bloku.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)