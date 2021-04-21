---
title: 'Postupy: použití barev v oblastech aplikace Excel prostřednictvím kódu programu'
description: Přečtěte si, že pokud chcete použít barvu na text v rámci rozsahu buněk, použijte ovládací prvek NamedRange nebo nativní objekt oblasti aplikace Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 081985dbd4b235fe5dd8d3472d0ab574603abe1b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828316"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Postupy: použití barev v oblastech aplikace Excel prostřednictvím kódu programu
  Chcete-li použít barvu na text v rámci rozsahu buněk, použijte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek nebo nativní objekt oblasti aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange
 Tento příklad je pro přizpůsobení na úrovni dokumentu.

### <a name="to-apply-color-to-a-namedrange-control"></a>Použití barvy pro ovládací prvek NamedRange

1. Vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek v buňce a1.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet65":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet65":::

2. Nastaví barvu textu v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacím prvku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet66":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet66":::

## <a name="use-native-excel-ranges"></a>Použít nativní oblasti aplikace Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Aplikování barvy na nativní objekt oblasti aplikace Excel

1. Vytvořte oblast v buňce a1 a pak nastavte barvu textu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
