---
title: Položka hostitele sešitu
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 797f1a55ec7632114e411bf0ba08e7f4e0cc146e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255087"
---
# <a name="workbook-host-item"></a>Položka hostitele sešitu
  Položka hostitele je typ, který <xref:Microsoft.Office.Interop.Excel.Workbook> rozšiřuje typ z primárního definičního sestavení pro Excel. <xref:Microsoft.Office.Tools.Excel.Workbook> Položka hostitele poskytuje všechny stejné vlastnosti, metody a události <xref:Microsoft.Office.Interop.Excel.Workbook> jako objekt, ale také poskytuje další funkce. <xref:Microsoft.Office.Tools.Excel.Workbook>

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V projektech na úrovni dokumentu je výchozí <xref:Microsoft.Office.Tools.Excel.Workbook> Hostitelská položka, která představuje sešit v projektu. V projektech doplňku VSTO můžete v době běhu generovat <xref:Microsoft.Office.Tools.Excel.Workbook> položky hostitele.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Porozumění položce hostitele sešitu v projektech na úrovni dokumentu
 Pro přístup k sešitu v projektu použijte `ThisWorkbook` třídu. Třída poskytuje přístup ke členům <xref:Microsoft.Office.Tools.Excel.Workbook> hostitelské položky k provádění základních úloh v přizpůsobení, jako je například spuštění kódu při otevření nebo zavření sešitu. `ThisWorkbook` Další informace najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 `ThisWorkbook` Třída poskytuje umístění, ve kterém můžete začít psát kód v projektu. Vzhledem k tomu, že třída poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Excel.Workbook> objekt v primárním sestavení vzájemné spolupráce pro aplikaci Excel, můžete použít `ThisWorkbook` také pro přístup k objektovému modelu aplikace Excel. Další informace najdete v tématu [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

 Dvojitým kliknutím na položku projektu **ThisWorkbook** v **Průzkumník řešení** zobrazíte návrháře sešitu a zobrazíte vlastnosti a události sešitu v okně **vlastnosti** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Omezení položky hostitele sešitu v projektech na úrovni dokumentu
 Projekt na úrovni dokumentu může obsahovat pouze jednu <xref:Microsoft.Office.Tools.Excel.Workbook> položku hostitele (tj `ThisWorkbook` . třídu). Nové <xref:Microsoft.Office.Tools.Excel.Workbook> položky hostitele nelze do projektu přidat v době návrhu a v době spuštění nelze vytvořit nové <xref:Microsoft.Office.Tools.Excel.Workbook> položky hostitele z přizpůsobení na úrovni dokumentu.

 Pokud vytvoříte nový sešit aplikace Excel v době běhu, bude tento typ <xref:Microsoft.Office.Interop.Excel.Workbook>. Protože se nejedná o hostitelskou položku, nemůže obsahovat žádné ovládací prvky hostitele ani ovládací prvky model Windows Forms. Další informace o vytváření sešitů v době běhu naleznete v [tématu How to: Vytváření nových sešitů](../vsto/how-to-programmatically-create-new-workbooks.md)prostřednictvím kódu programu

 <xref:Microsoft.Office.Tools.Excel.Workbook> Hostitelská položka neslouží jako kontejner pro hostitelské ovládací prvky. Proto nelze do sešitu přidat žádné viditelné ovládací prvky, ale můžete přidat součásti, <xref:System.Data.DataSet>jako například, aby mohly být součásti sdíleny všemi listy. V projektu na úrovni dokumentu lze součásti dostupné pro sešit najít na kartě **Komponenta** , na kartě **data** a na kartě **model Windows Forms** v **sadě nástrojů**.

> [!NOTE]
> Vývojové nástroje pro Office v sadě Visual Studio nepodporují Sdílené sešity.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Porozumění položkám hostitele sešitu v projektech doplňku VSTO
 V projektech doplňku VSTO můžete vygenerovat <xref:Microsoft.Office.Tools.Excel.Workbook> položku hostitele v době běhu pro libovolný sešit, který je otevřen v aplikaci Excel. Chcete-li <xref:Microsoft.Office.Tools.Excel.Workbook> vygenerovat položku hostitele, `GetVstoObject` použijte metodu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Viz také:
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
