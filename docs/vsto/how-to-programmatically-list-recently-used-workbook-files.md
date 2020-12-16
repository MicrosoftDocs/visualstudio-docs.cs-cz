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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bbcad553ade6234d3a688c8f718a0dd6e6cda509
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525630"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Postupy: zobrazení seznamu naposledy použitých souborů sešitů prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>Vlastnost vrátí kolekci, která obsahuje názvy všech souborů, které se zobrazí v seznamu systém Microsoft Office Excel naposledy použitých souborů. Délka seznamu se liší v závislosti na počtu souborů, které uživatel zvolil pro zachování. Výsledky můžete zobrazit v rozsahu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Výpis naposledy použitých sešitů v objektu Range

1. Projde seznam posledních souborů a zobrazí názvy v buňkách relativně k <xref:Microsoft.Office.Interop.Excel.Range> objektu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
