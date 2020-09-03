---
title: Položka hostitele listu
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 301b0a62efae4674432b1051451e5d982899c1b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254874"
---
# <a name="worksheet-host-item"></a>Položka hostitele listu
  <xref:Microsoft.Office.Tools.Excel.Worksheet>Položka hostitele je typ, který rozšiřuje <xref:Microsoft.Office.Interop.Excel.Worksheet> typ z primárního definičního sestavení pro Excel. <xref:Microsoft.Office.Tools.Excel.Worksheet>Položka hostitele poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt, ale také zpřístupňuje další události a funguje jako kontejner pro ovládací prvky hostitele a model Windows Forms ovládací prvky.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V projektech na úrovni dokumentu můžete v <xref:Microsoft.Office.Tools.Excel.Worksheet> době návrhu přidat do projektu položky hostitele. V projektech doplňku VSTO můžete v <xref:Microsoft.Office.Tools.Excel.Worksheet> době běhu generovat položky hostitele.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Porozumění položkám hostitele na listu v projektech na úrovni dokumentu
 Když vytvoříte projekt na úrovni dokumentu pro aplikaci Excel, Visual Studio automaticky vytvoří tři <xref:Microsoft.Office.Tools.Excel.Worksheet> položky hostitele v projektu. Výchozí názvy listů jsou `Sheet1` , `Sheet2` a `Sheet3` . Pokud vytvoříte projekt založený na existujícím sešitu, počet položek hostitele závisí na počtu listů v sešitu.

 Tyto třídy listů umožňují přístup ke členům <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelské položky, aby bylo možné provádět základní úkoly v rámci přizpůsobení, jako je například úprava obsahu listu. Tyto třídy můžete použít také k přidání ovládacích prvků do listů. Kombinací různých sad ovládacích prvků a psaní kódu můžete navazovat ovládací prvky na data, shromažďovat informace od uživatele a reagovat na akce uživatele. Další informace najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 Třídy listu poskytují umístění, ve kterém můžete začít psát kód v projektu. Vzhledem k tomu, že třída poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt v primárním sestavení vzájemné spolupráce pro aplikaci Excel, můžete tyto třídy použít také pro přístup k objektovému modelu aplikace Excel. Další informace najdete v tématu [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

 V projektech na úrovni dokumentu můžete do projektu přidat další <xref:Microsoft.Office.Tools.Excel.Worksheet> položky hostitele v době návrhu přidáním nového listu do sešitu v návrháři.

### <a name="rename-worksheets"></a>Přejmenování listů
 V projektu na úrovni dokumentu můžete přejmenovat listy v návrháři aplikace Visual Studio, ale tím se pouze změní zobrazovaný název listu. Programový název je stále výchozím názvem listu. Pokud list přejmenujete v okně **vlastnosti** , změní se pouze programový název.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Omezení položky hostitele listu v projektech na úrovni dokumentu
 <xref:Microsoft.Office.Tools.Excel.Worksheet>V projektu na úrovni dokumentu nelze vytvořit nové položky hostitele v době běhu. Pokud vytvoříte nový list aplikace Excel v době běhu, bude to typ <xref:Microsoft.Office.Interop.Excel.Worksheet> . Protože se nejedná o hostitelskou položku, nemůže obsahovat žádné ovládací prvky hostitele ani ovládací prvky model Windows Forms. Další informace o vytváření dokumentů v době běhu naleznete v tématu [How to: programing forming New Listes do sešitů](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Porozumění položkám hostitele v sešitech v projektech doplňku VSTO
 V projektech na úrovni aplikace můžete vygenerovat <xref:Microsoft.Office.Tools.Excel.Worksheet> položku hostitele v době běhu pro libovolný list, který je otevřen v aplikaci Excel. Můžete použít <xref:Microsoft.Office.Tools.Excel.Worksheet> položku hostitele k přidání ovládacích prvků do přidruženého listu nebo pro zpracování událostí, které nejsou k dispozici pro <xref:Microsoft.Office.Interop.Excel.Worksheet> objekty.

 Chcete-li vygenerovat <xref:Microsoft.Office.Tools.Excel.Worksheet> položku hostitele, použijte `GetVstoObject` metodu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Viz také
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Položka hostitele sešitu](../vsto/workbook-host-item.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
