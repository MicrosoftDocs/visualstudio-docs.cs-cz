---
title: 'Postupy: Přidání ovládacích prvků ListObject do listů'
description: Naučte se, jak přidat ovládací prvky ListObject do listu aplikace systém Microsoft Office Excel v době návrhu a v době běhu v projektech na úrovni dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c790117c907144b9edc141463b8f7751a544a10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954238"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Postupy: Přidání ovládacích prvků ListObject do listů
  <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvky můžete přidat do listu aplikace systém Microsoft Office Excel v době návrhu a v době běhu v projektech na úrovni dokumentu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Můžete také přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvky v době běhu v projektech doplňku VSTO.

 V tomto tématu jsou popsány následující úlohy:

- [Přidat ovládací prvky ListObject v době návrhu](#designtime)

- [Přidání ovládacích prvků ListObject v době běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Přidání ovládacích prvků ListObject v době běhu v projektu doplňku VSTO](#runtimeaddin)

  Další informace o <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvcích naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Přidat ovládací prvky ListObject v době návrhu
 Existuje několik způsobů, jak přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvky do listu v projektu na úrovni dokumentu v době návrhu: v aplikaci Excel, v sadě **nástrojů sady** Visual Studio a v okně **zdroje dat** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Používání pásu karet v aplikaci Excel

1. Na kartě **Vložit** ve skupině **tabulky** klikněte na **tabulka**.

2. Vyberte buňku nebo buňky, které chcete zahrnout do seznamu, a klikněte na tlačítko **OK**.

#### <a name="to-use-the-toolbox"></a>Použití panelu nástrojů

1. Z karty **ovládací prvky aplikace Excel** na **panelu nástrojů** přetáhněte <xref:Microsoft.Office.Tools.Excel.ListObject> na list.

     Zobrazí se dialogové okno **Přidat ovládací prvek ListObject** .

2. Vyberte buňku nebo buňky, které chcete zahrnout do seznamu, a klikněte na tlačítko **OK**.

     Pokud nechcete zachovat výchozí název, můžete název změnit v okně **vlastnosti** .

#### <a name="to-use-the-data-sources-window"></a>Použití okna zdroje dat

1. Otevřete okno **zdroje dat** a vytvořte zdroj dat pro projekt. Další informace najdete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

2. Přetáhněte tabulku z okna **zdroje dat** do listu.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Do listu je přidán ovládací prvek vázaný na data. Další informace najdete v tématu [datové vazby a model Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Přidání ovládacích prvků ListObject v době běhu v projektu na úrovni dokumentu
 Ovládací prvek lze přidat <xref:Microsoft.Office.Tools.Excel.ListObject> dynamicky v době běhu. To umožňuje vytvořit hostitelské ovládací prvky v reakci na události. Dynamicky vytvořené objekty seznamu se v listu neukládají jako hostitelské ovládací prvky při zavření listu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Postup přidání ovládacího prvku ListObject do listu prostřednictvím kódu programu

1. V <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužné rutině události pro `Sheet1` vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku do buněk **a1** až **a4**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Přidání ovládacích prvků ListObject v době běhu v projektu doplňku VSTO
 Ovládací prvek můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> programově do libovolného otevřeného listu v projektu doplňku VSTO. Dynamicky vytvořené objekty seznamu se v listu neukládají jako hostitelské ovládací prvky, když je sešit uložený a pak uzavřený. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Postup přidání ovládacího prvku ListObject do listu prostřednictvím kódu programu

1. Následující kód vygeneruje položku hostitele listu, která je založena na otevřeném listu, a poté přidá <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek do buněk **a1** až **a4**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]

## <a name="see-also"></a>Viz také
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
