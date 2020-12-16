---
title: 'Postupy: Změna velikosti ovládacích prvků v buňkách listu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio změnit velikost ovládacích prvků v rámci buněk listu aplikace Microsoft Excel v době návrhu i v době běhu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ba2a77dc44618c0415e645718aff3ead542b4b48
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525348"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Postupy: Změna velikosti ovládacích prvků v buňkách listu
  Když změníte velikost sloupců nebo řádků na listu, všechny ovládací prvky hostitele v buňkách se automaticky změní na výšku nebo šířku buňky, u které se změnila velikost. Ovládací prvky model Windows Forms ve výchozím nastavení automaticky nemění velikost.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pokud přidáte ovládací prvky v době návrhu, je nutné nastavit možnosti umístění pro každý ovládací prvek.

 Pokud přidáte ovládací prvek model Windows Forms programově a zadáte argument rozsahu, ovládací prvek automaticky změní velikost při změně velikosti buňky v rozsahu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Změnit velikost ovládacích prvků v době návrhu

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Chcete-li změnit velikost ovládacích prvků s buňkami v době návrhu

1. Z **panelu nástrojů** přetáhněte ovládací prvek model Windows Forms do listu.

2. Klikněte pravým tlačítkem myši na ovládací prvek a potom klikněte na možnost **Formát ovládacího prvku**.

3. V dialogovém okně **Formát ovládacího prvku** klikněte na kartu **vlastnosti** .

4. V části **umístění objektu** vyberte možnost **přesunout a velikost s buňkami** a pak klikněte na tlačítko **OK**.

     Když změníte velikost buňky, která obsahuje ovládací prvek, ovládací prvek změní velikost tak, aby odpovídala buňce.

## <a name="resize-controls-at-run-time"></a>Změnit velikost ovládacích prvků za běhu
 Pokud přidáte model Windows Forms ovládací prvek za běhu a předáte ho <xref:Microsoft.Office.Interop.Excel.Range> jako umístění pro ovládací prvek, ovládací prvek se změní automaticky, když se změní velikost buňky listu, která obsahuje rozsah.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Chcete-li změnit velikost ovládacích prvků na buňky v době běhu

1. Přidejte ovládací prvek do rozsahu a1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Když změníte velikost buňky, která obsahuje ovládací prvek, ovládací prvek změní velikost tak, aby odpovídala buňce.

## <a name="reset-control-placement"></a>Resetovat umístění ovládacího prvku
 Umístění a změnu velikosti ovládacího prvku můžete obnovit nastavením `Placement` vlastnosti na jednu z následujících <xref:Microsoft.Office.Interop.Excel.XlPlacement> hodnot:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Změna chování ovládacího prvku tak, aby se nezměnila velikost ani přesun s buňkou

1. Zavolejte vlastnost umístění ovládacího prvku a nastavte hodnotu na <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Viz také
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Postupy: skrytí ovládacích prvků na listech při tisku](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
