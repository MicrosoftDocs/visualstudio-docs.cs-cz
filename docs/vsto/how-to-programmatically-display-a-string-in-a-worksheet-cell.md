---
title: 'Postupy: zobrazení řetězce v buňce listu prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově zobrazit řetězec v buňce listu Microsoft Excelu pomocí ovládacího prvku NamedRange nebo nativního objektu Range Excelu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a7bc48df6e30381ff275b9f11dabe04a25d6dd7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825924"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Postupy: zobrazení řetězce v buňce listu prostřednictvím kódu programu
  Tento příklad ukazuje, jak zobrazit text v buňce programově. Chcete-li zobrazit text v buňce, použijte buď <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek, nebo nativní objekt excelového rozsahu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange
 V tomto příkladu se používá <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `message` . Ovládací prvek musí být přidán do přizpůsobení na úrovni dokumentu v době návrhu. Následující kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

### <a name="to-display-text-in-a-namedrange-control"></a>Zobrazení textu v ovládacím prvku NamedRange

1. Nastavte hodnotu <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku na **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Použít nativní rozsah aplikace Excel
 Následující kód vytvoří nový rozsah programově a pak mu přiřadí hodnotu.

### <a name="to-display-text-in-an-excel-range"></a>Zobrazení textu v oblasti aplikace Excel

1. Načtěte rozsah v buňce **a1** `Sheet1` a nastavte hodnotu na **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Viz také
- [Návod: shromáždění dat pomocí formuláře Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Řešení potíží s řešeními pro systém Office](../vsto/troubleshooting-office-solutions.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
