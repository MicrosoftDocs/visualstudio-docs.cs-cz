---
title: Položka hostitele sešitu
description: Přečtěte si, že položka hostitele sešitu je typ, který rozšiřuje typ sešitu z primárního definičního sestavení pro aplikaci Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24f32f8799d2bac5c23a0f8a2ef92857d2a6f7c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847593"
---
# <a name="workbook-host-item"></a>Položka hostitele sešitu
  <xref:Microsoft.Office.Tools.Excel.Workbook>Položka hostitele je typ, který rozšiřuje <xref:Microsoft.Office.Interop.Excel.Workbook> typ z primárního definičního sestavení pro Excel. <xref:Microsoft.Office.Tools.Excel.Workbook>Položka hostitele poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Excel.Workbook> objekt, ale také poskytuje další funkce.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V projektech na úrovni dokumentu je výchozí <xref:Microsoft.Office.Tools.Excel.Workbook> Hostitelská položka, která představuje sešit v projektu. V projektech doplňku VSTO můžete v <xref:Microsoft.Office.Tools.Excel.Workbook> době běhu generovat položky hostitele.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Porozumění položce hostitele sešitu v projektech na úrovni dokumentu
 Pro přístup k sešitu v projektu použijte `ThisWorkbook` třídu. `ThisWorkbook`Třída poskytuje přístup ke členům <xref:Microsoft.Office.Tools.Excel.Workbook> hostitelské položky k provádění základních úloh v přizpůsobení, jako je například spuštění kódu při otevření nebo zavření sešitu. Další informace najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 `ThisWorkbook`Třída poskytuje umístění, ve kterém můžete začít psát kód v projektu. Vzhledem k tomu, že třída poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Excel.Workbook> objekt v primárním sestavení vzájemné spolupráce pro aplikaci Excel, můžete použít také `ThisWorkbook` pro přístup k objektovému modelu aplikace Excel. Další informace najdete v tématu [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

 Dvojitým kliknutím na položku projektu **ThisWorkbook** v **Průzkumník řešení** zobrazíte návrháře sešitu a zobrazíte vlastnosti a události sešitu v okně **vlastnosti** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Omezení položky hostitele sešitu v projektech na úrovni dokumentu
 Projekt na úrovni dokumentu může obsahovat pouze jednu <xref:Microsoft.Office.Tools.Excel.Workbook> položku hostitele (tj `ThisWorkbook` . třídu). Nové <xref:Microsoft.Office.Tools.Excel.Workbook> položky hostitele nelze do projektu přidat v době návrhu a v době spuštění nelze vytvořit nové <xref:Microsoft.Office.Tools.Excel.Workbook> položky hostitele z přizpůsobení na úrovni dokumentu.

 Pokud vytvoříte nový sešit aplikace Excel v době běhu, bude tento typ <xref:Microsoft.Office.Interop.Excel.Workbook> . Protože se nejedná o hostitelskou položku, nemůže obsahovat žádné ovládací prvky hostitele ani ovládací prvky model Windows Forms. Další informace o vytváření sešitů za běhu najdete v tématu [Postupy: vytváření nových sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-workbooks.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook>Hostitelská položka neslouží jako kontejner pro hostitelské ovládací prvky. Proto nelze do sešitu přidat žádné viditelné ovládací prvky, ale můžete přidat součásti, jako například <xref:System.Data.DataSet> , aby mohly být součásti sdíleny všemi listy. V projektu na úrovni dokumentu lze součásti dostupné pro sešit najít na kartě **Komponenta** , na kartě **data** a na kartě **model Windows Forms** v **sadě nástrojů**.

> [!NOTE]
> Vývojové nástroje pro Office v sadě Visual Studio nepodporují Sdílené sešity.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Porozumění položkám hostitele sešitu v projektech doplňku VSTO
 V projektech doplňku VSTO můžete vygenerovat <xref:Microsoft.Office.Tools.Excel.Workbook> položku hostitele v době běhu pro libovolný sešit, který je otevřen v aplikaci Excel. Chcete-li vygenerovat <xref:Microsoft.Office.Tools.Excel.Workbook> položku hostitele, použijte `GetVstoObject` metodu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Viz také
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
