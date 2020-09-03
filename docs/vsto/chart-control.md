---
title: Ovládací prvek grafu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 864422aac695fbf474e6ed6b8cf6d765247eabf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255305"
---
# <a name="chart-control"></a>Ovládací prvek grafu
  <xref:Microsoft.Office.Tools.Excel.Chart>Ovládací prvek je objekt grafu, který zpřístupňuje události. Když přidáte graf na list, Visual Studio vytvoří <xref:Microsoft.Office.Tools.Excel.Chart> objekt, který lze naprogramovat přímo, aniž by bylo nutné procházet model systém Microsoft Office excelového objektu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Vytvoření ovládacího prvku
 <xref:Microsoft.Office.Tools.Excel.Chart>Ovládací prvky můžete přidat do listu aplikace systém Microsoft Office Excel v době návrhu nebo v době běhu v projektu na úrovni dokumentu.

 <xref:Microsoft.Office.Tools.Excel.Chart>V doplňku VSTO můžete do listu přidat ovládací prvky v době běhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Dynamicky vytvořené objekty grafu se v listu neukládají jako hostitelské ovládací prvky při zavření listu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="formatting"></a>Formátování
 <xref:Microsoft.Office.Interop.Excel.Chart>Pro ovládací prvek lze také použít veškeré formátování, které lze použít na objekt <xref:Microsoft.Office.Tools.Excel.Chart> . To zahrnuje ohraničení, písma, typ grafu, mřížky, legendu a popisky dat.

## <a name="events"></a>Události
 Pro ovládací prvek jsou k dispozici následující události <xref:Microsoft.Office.Tools.Excel.Chart> :

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>Viz také
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
