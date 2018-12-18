---
title: Hostitelská položka Worksheet
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4052e7d9b096d9bae6671834369ece6d31bee4a0
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258915"
---
# <a name="worksheet-host-item"></a>Hostitelská položka Worksheet
  <xref:Microsoft.Office.Tools.Excel.Worksheet> Hostitelská položka je typ, který rozšiřuje <xref:Microsoft.Office.Interop.Excel.Worksheet> typu ze sestavení primární spolupráce pro aplikaci Excel. <xref:Microsoft.Office.Tools.Excel.Worksheet> Hostitelská položka poskytuje všechny stejné vlastnosti, metod a události <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu, ale také zpřístupní další události a slouží jako kontejner pro hostitele a ovládacích prvků Windows Forms.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Projekty na úrovni dokumentu, můžete přidat <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položek do projektu v době návrhu. V doplňku VSTO projekty, můžete vygenerovat <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položky v době běhu.  
  
## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Pochopení list – hostitelské položky v projekty na úrovni dokumentu  
 Když vytvoříte projekt na úrovni dokumentu pro Excel, Visual Studio automaticky vytvoří tři <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položky v projektu. Výchozí názvy sešitů jsou `Sheet1`, `Sheet2`, a `Sheet3`. Pokud vytvoříte projekt založený na existující sešit, počet položek hostitele, které závisí na počtu listů v sešitu.  
  
 Tyto třídy listu umožňují přístup k členy <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka provádět základní úkoly ve vašem vlastním přizpůsobení, jako je například úprava obsah listu. Tyto třídy můžete také použít k přidávání ovládacích prvků do listů. Kombinování různé sady ovládacích prvků a psaní kódu, že ovládací prvky můžete vázat na data, shromáždit informace od uživatele a reagovat na akce uživatele. Další informace najdete v tématu [programu úpravy na úrovni dokumentů](../vsto/programming-document-level-customizations.md).  
  
 Třídy listu zadejte umístění, ve kterém můžete spustit psaní kódu v projektu. Protože třída poskytuje všechny stejné vlastnosti, metod a události, jako <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu v primární spolupracující sestavení pro aplikaci Excel, můžete také použít tyto třídy pro přístup k modelu objektů aplikace Excel. Další informace najdete v tématu [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  
  
 Projekty na úrovni dokumentu, můžete přidat další <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položek do projektu v době návrhu tak, že přidáte do nového sešitu v sešitu v návrháři.  
  
### <a name="rename-worksheets"></a>Přejmenování listů  
 V projektech na úrovni dokumentu můžete přejmenovat listy v návrháři Visual Studio, ale tato operace změní jenom zobrazovaný název listu. Programový název je stále výchozí název listu. Pokud přejmenujete na listu v **vlastnosti** okně jenom programové název mění.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Omezení hostitelská položka worksheet v projekty na úrovni dokumentu  
 Nelze vytvořit nový <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položky v době běhu v projektech na úrovni dokumentu. Pokud vytvoříte nový sešit aplikace Excel. v době běhu, bude typu <xref:Microsoft.Office.Interop.Excel.Worksheet>. Protože není položku hostitele, nemůže obsahovat žádné hostitelské ovládací prvky nebo ovládací prvky Windows Forms. Další informace o vytváření dokumentů v době běhu najdete v tématu [postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Pochopení list – hostitelské položky v projekty doplňku VSTO  
 V projektech na úrovni aplikace, můžete vygenerovat <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položky v době běhu pro všechny listu, která je otevřít v aplikaci Excel. Můžete použít <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka k přidávání ovládacích prvků do přidružených listu, nebo události, které nejsou k dispozici na <xref:Microsoft.Office.Interop.Excel.Worksheet> objekty.  
  
 Generovat <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka, použijte `GetVstoObject` metoda. Další informace najdete v tématu [dokumentů rozšířit aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Viz také:  
 [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Hostitelská položka Workbook](../vsto/workbook-host-item.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  