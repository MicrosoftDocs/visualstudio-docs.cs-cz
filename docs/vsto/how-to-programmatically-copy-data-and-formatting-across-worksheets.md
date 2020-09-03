---
title: Kopírování dat a formátování mezi listy prostřednictvím kódu programu
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 07baa23b6fd276e8fb8452934dc6361544d16038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546104"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Postupy: kopírování dat a formátování mezi listy prostřednictvím kódu programu
  Data z rozsahu na jednom listu můžete kopírovat do všech ostatních listů v sešitu pomocí <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metody. Zadejte rozsah a určete, zda chcete kopírovat data, formátování nebo obojí.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje rozsah s názvem `rangeData` v listu.

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Postupy: Změna formátování řádků listů obsahujících vybrané buňky prostřednictvím kódu programu](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
