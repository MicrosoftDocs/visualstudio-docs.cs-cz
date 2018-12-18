---
title: 'Postupy: zobrazování řetězec v buňkách listů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 336ab67cd5c63a912d72b0fce3fa73c9fca5184f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256816"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Postupy: zobrazování řetězec v buňkách listů prostřednictvím kódu programu
  Tento příklad ukazuje, jak zobrazit text v buňce prostřednictvím kódu programu. Chcete-li zobrazit text v buňce, použijte buď <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek nebo objekt rozsahu nativní aplikace Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange  
 Tento příklad používá <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `message`. Ovládací prvek musí být přidaný do přizpůsobení úrovni dokumentu v době návrhu. Následující kód musí být umístěny v listu třída, není v `ThisWorkbook` třídy.  
  
### <a name="to-display-text-in-a-namedrange-control"></a>K zobrazení textu v ovládacím prvku NamedRange  
  
1.  Nastavte hodnotu <xref:Microsoft.Office.Tools.Excel.NamedRange> řídit k **Hello, World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="use-a-native-excel-range"></a>Použít nativní oblasti aplikace Excel  
 Následující kód vytvoří nový rozsah prostřednictvím kódu programu a potom k němu přiřadí hodnotu.  
  
### <a name="to-display-text-in-an-excel-range"></a>Zobrazení textu v oblasti aplikace Excel  
  
1.  Načtení rozsahu na buňky **A1** na `Sheet1` a nastavte hodnotu na **Hello, World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Shromažďování dat pomocí formuláře Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Řešení potíží s řešení pro systém Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange – ovládací prvek](../vsto/namedrange-control.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  