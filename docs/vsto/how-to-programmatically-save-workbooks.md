---
title: 'Postupy: ukládání sešitů prostřednictvím kódu programu'
description: Programové ukládání sešitů aplikace Microsoft Excel beze změny cesty a uložení kopie sešitu, aniž by bylo nutné upravovat otevřený sešit v paměti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbc228a703d6c9224fda545a93132ccb45c94b0f
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524627"
---
# <a name="how-to-programmatically-save-workbooks"></a>Postupy: ukládání sešitů prostřednictvím kódu programu
  Existuje několik způsobů, jak sešit uložit. Sešit můžete uložit beze změny cesty. Pokud sešit ještě nebyl uložen, uložte ho zadáním cesty. Bez explicitní cesty systém Microsoft Office Excel uloží soubor do aktuální složky s názvem, který jste zadali při jeho vytvoření. Můžete také uložit kopii sešitu beze změny otevřeného sešitu v paměti.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Uložení sešitu beze změny cesty

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Uložení sešitu přidruženého k přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> metodu `ThisWorkbook` třídy.

     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Uložení aktivního sešitu v doplňku VSTO

1. Voláním <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> metody uložte aktivní sešit. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisAddIn` třídě v projektu doplňku VSTO pro Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]

## <a name="save-a-workbook-with-a-new-path"></a>Uložení sešitu s novou cestou
 Zadaný sešit můžete uložit do nového umístění nebo s novým názvem, volitelně zadat formát souboru, heslo, režim přístupu a další.

> [!NOTE]
> Chcete-li <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> Uložit sešit s novou cestou, je vhodné nastavit vlastnost na **hodnotu false** , protože uložení v některých formátech vyžaduje interakci. Nastavení této vlastnosti na **hodnotu false** způsobí, že aplikace Excel použije všechny výchozí hodnoty.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Uložení sešitu přidruženého k přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodu `ThisWorkbook` třídy. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisWorkbook` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Uložení aktivního sešitu v doplňku VSTO

1. Voláním <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> metody uložte aktivní sešit do nové cesty. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisAddIn` třídě v projektu doplňku VSTO pro Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]

## <a name="save-a-copy-of-the-workbook"></a>Uložit kopii sešitu
 Kopii sešitu můžete uložit do souboru bez změny otevřeného sešitu v paměti. To je užitečné, když chcete vytvořit záložní kopii bez změny umístění sešitu.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Uložení sešitu přidruženého k přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> metodu `ThisWorkbook` třídy. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisWorkbook` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Uložení aktivního sešitu v doplňku VSTO

1. Voláním <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> metody uložte kopii aktivního sešitu. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisAddIn` třídě v projektu doplňku VSTO pro Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]

## <a name="robust-programming"></a>Robustní programování
 Při interaktivním zrušení jakékoli metody, která ukládá nebo kopíruje sešit, se ve vašem kódu vyvolá chyba za běhu. Například Pokud procedura volá <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodu, ale nezakáže výzvy z Excelu a uživatel klikne na **Zrušit** po zobrazení výzvy, Excel vyvolá chybu za běhu.

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Položka hostitele sešitu](../vsto/workbook-host-item.md)
- [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
