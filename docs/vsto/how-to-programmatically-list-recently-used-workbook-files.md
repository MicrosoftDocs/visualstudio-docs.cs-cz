---
title: 'Postupy: zobrazení seznamu naposledy použitých souborů sešitů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově vypsat nedávno použité soubory sešitu Microsoft Excelu pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba7ca717af4330e8fb3c102b3a5fe5bf7d9162b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825326"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Postupy: zobrazení seznamu naposledy použitých souborů sešitů prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>Vlastnost vrátí kolekci, která obsahuje názvy všech souborů, které se zobrazí v seznamu systém Microsoft Office Excel naposledy použitých souborů. Délka seznamu se liší v závislosti na počtu souborů, které uživatel zvolil pro zachování. Výsledky můžete zobrazit v rozsahu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Výpis naposledy použitých sešitů v objektu Range

1. Projde seznam posledních souborů a zobrazí názvy v buňkách relativně k <xref:Microsoft.Office.Interop.Excel.Range> objektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
