---
title: Automatizace aplikace Excel s použitím rozšířených objektů
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0a74c5a62cc2e14615db8dd17c9a34a7e54178e7
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248043"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automatizace aplikace Excel s použitím rozšířených objektů
  Při vývoji řešení pro aplikaci Excel v sadě Visual Studio, můžete použít *hostovat položky* a *hostování ovládacího prvku*s ve vašich řešeních. Jedná se o objekty, které rozšiřují některé běžně používané objekty v objektovém modelu (to znamená, objektový model, který je zveřejněný prostřednictvím sestavení primární spolupráce pro aplikace Excel), Excel, jako <xref:Microsoft.Office.Interop.Excel.Worksheet> a <xref:Microsoft.Office.Interop.Excel.Range> objekty. Rozšířené objekty se chovají jako objekty aplikace Excel, které jsou založeny na, ale přidávají další funkce, jako je nové události a možnosti vázání dat na objekty.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Jsou k dispozici v obou doplňku VSTO hostitelských položek a hostitelských ovládacích prvků a úrovni dokumentu přizpůsobení, i když kontext, ve kterém ty je možné použít se liší pro každý typ řešení. Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="excel-host-items"></a>Excel hostitelské položky  
 Projekty aplikace Excel poskytují přístup k několika hostitelské položky:  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Tato položka hostitele obsahuje a představuje listu v projektu. Taky funguje jako kontejner pro spravované ovládací prvky, včetně hostitelské ovládací prvky a ovládací prvky Windows Forms, a udržuje informace o ovládacích prvcích na svém povrchu. Další informace najdete v tématu [hostitelská položka Worksheet](../vsto/worksheet-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Tato položka hostitele představuje sešitu ve vašem projektu a funguje jako kontejner pro komponenty, které jsou sdíleny ve všech listů v sešitu. Další informace najdete v tématu [hostitelská položka Workbook](../vsto/workbook-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Tento hostitel položka sešitu v Excelu, který obsahuje pouze grafu a zpřístupní události.  
  
     Když přidáte list s grafem v době návrhu jako nový list ve vašem projektu přizpůsobení na úrovni dokumentu aplikace Microsoft Office Excel, sada Visual Studio automaticky vytvoří <xref:Microsoft.Office.Tools.Excel.ChartSheet> hostitelský objekt.  
  
     I když <xref:Microsoft.Office.Tools.Excel.ChartSheet> hostitelský objekt je listu aplikace Excel, všechny ovládací prvky nelze přidat do listu s grafem. Pokud chcete mít další ovládací prvky na listu s grafem, nepoužívejte list s grafem. Místo toho můžete umístit grafu jako vložený objekt na listu s použitím <xref:Microsoft.Office.Tools.Excel.Chart> hostování ovládacího prvku. Další informace najdete v tématu [ovládacího prvku grafu](../vsto/chart-control.md).  
  
## <a name="excel-host-controls"></a>hostitelské ovládací prvky aplikace Excel  
 Existuje několik hostitelů ovládací prvky pro Excel, které vám pomůžou vytvářet, organizovat a automatizovat pracovní sešity a listy nástroje. Tyto ovládací prvky hostitele poskytnout události a datové vazby, které nemají jejich protějšky v nativní objektovému modelu Excelu.  
  
 Další informace o hostitelské ovládací prvky, které můžete použít v projektech aplikace Excel naleznete v následujících tématech:  
  
-   [Graf – ovládací prvek](../vsto/chart-control.md)  
  
-   [ListObject – ovládací prvek](../vsto/listobject-control.md)  
  
-   [Namedrange – ovládací prvek](../vsto/namedrange-control.md)  
  
-   [Xmlmappedrange – ovládací prvek](../vsto/xmlmappedrange-control.md)  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Vyplnění ovládacích prvků ListObject daty](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Postupy: Přidání ovládacích prvků graf do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Postupy: Přidání ovládacích prvků XMLMappedRange do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Postupy: Ověření dat při přidání nového řádku do ovládacího prvku ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Postupy: Mapování sloupců objektu ListObject na data](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Návod: Program ošetření událostí ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
