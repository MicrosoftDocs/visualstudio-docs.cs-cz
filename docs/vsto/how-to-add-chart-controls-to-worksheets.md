---
title: 'Postupy: Přidání ovládacích prvků grafu do listů'
description: Naučte se, jak můžete přidat ovládací prvky grafu do systém Microsoft Office excelového listu v době návrhu a za běhu v přizpůsobení na úrovni dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88ebe38a881e148f10149189a2d27ac81bd0ddc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827029"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Postupy: Přidání ovládacích prvků grafu do listů
  <xref:Microsoft.Office.Tools.Excel.Chart>Ovládací prvky můžete přidat do listu aplikace systém Microsoft Office Excel v době návrhu a v době běhu v přizpůsobení na úrovni dokumentu. Můžete také přidat <xref:Microsoft.Office.Tools.Excel.Chart> ovládací prvky v době běhu v doplňkech VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V tomto tématu jsou popsány následující úlohy:

- [Přidat ovládací prvky grafu v době návrhu](#designtime)

- [Přidat ovládací prvky grafu za běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Přidání ovládacích prvků Chart v době běhu v projektu doplňku VSTO](#runtimeaddin)

  Další informace o <xref:Microsoft.Office.Tools.Excel.Chart> ovládacích prvcích naleznete v tématu [Chart Control](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Přidat ovládací prvky grafu v době návrhu
 Ovládací prvek můžete přidat <xref:Microsoft.Office.Tools.Excel.Chart> do listu stejným způsobem, jako byste graf přidali v rámci aplikace.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.Chart>Ovládací prvek není k dispozici v okně **Sada nástrojů** nebo **zdroje dat** .

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Přidání ovládacího prvku pro hostování grafu do listu v aplikaci Excel

1. Na kartě **Vložit** ve skupině **grafy** klikněte na **sloupec**, klikněte na kategorii grafů a potom klikněte na požadovaný typ grafu.

2. V dialogovém okně **Vložit graf** klikněte na tlačítko **OK**.

3. Na kartě **Návrh** ve skupině **data** klikněte na **Vybrat data**.

4. V dialogovém okně **Vybrat zdroj dat** klikněte na pole **oblast dat** **grafu** a zrušte zaškrtnutí všech výchozích výběrů.

5. V tabulce **data pro graf** vyberte oblast buněk obsahující data pro graf (buňky **a5** až **D8**).

6. V dialogovém okně **Vybrat zdroj dat** klikněte na tlačítko **OK**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Přidat ovládací prvky grafu za běhu v projektu na úrovni dokumentu
 Ovládací prvek lze přidat <xref:Microsoft.Office.Tools.Excel.Chart> dynamicky v době běhu. Po zavření dokumentu se v dokumentu neukládají dynamicky vytvořené grafy jako hostitelské ovládací prvky. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Postup pro přidání ovládacího prvku grafu do listu prostřednictvím kódu programu

1. V <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužné rutině události pro `Sheet1` vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Excel.Chart> ovládacího prvku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet1":::

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Přidání ovládacích prvků Chart v době běhu v projektu doplňku VSTO
 Ovládací prvek můžete přidat <xref:Microsoft.Office.Tools.Excel.Chart> programově do libovolného otevřeného listu v projektu doplňku VSTO. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 Dynamicky vytvořené ovládací prvky grafu se v listu neukládají jako hostitelské ovládací prvky při zavření listu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Postup pro přidání ovládacího prvku grafu do listu prostřednictvím kódu programu

1. Následující kód vygeneruje položku hostitele listu, která je založena na otevřeném listu, a poté přidá <xref:Microsoft.Office.Tools.Excel.Chart> ovládací prvek.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet9":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad má následující požadavky:

- Data, která se mají vynést do grafu, se ukládají v rozsahu od A5 do D8 v listu.

## <a name="see-also"></a>Viz také
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Ovládací prvek grafu](../vsto/chart-control.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
