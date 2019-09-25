---
title: Automatizace Excelu pomocí rozšířených objektů
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65734f5397bae8c35fb8e312041d0600b8fa84e9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254334"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automatizace Excelu pomocí rozšířených objektů
  Při vývoji řešení v aplikaci Excel v aplikaci Visual Studio můžete použít *hostitelské položky* a *hostitelské řízení*s ve vašich řešeních. Jedná se o objekty, které rozšířily určité běžně používané objekty v objektovém modelu aplikace Excel (tj. objektový model, který je zveřejněn v rámci primárního definičního sestavení pro aplikaci Excel <xref:Microsoft.Office.Interop.Excel.Worksheet> ) <xref:Microsoft.Office.Interop.Excel.Range> , jako jsou například objekty a. Rozšířené objekty se chovají jako objekty aplikace Excel, na kterých jsou založeny, ale přidávají další funkce, jako jsou například nové události a funkce vazby dat do objektů.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Hostitelské položky a hostitelské ovládací prvky jsou k dispozici v doplňku VSTO i v přizpůsobení na úrovni dokumentu, i když kontext, ve kterém je lze použít, je pro každý typ řešení odlišný. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Položky hostitele Excelu
 Projekty aplikace Excel vám umožní přístup k několika položkám hostitele:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Tato položka hostitele obsahuje a představuje list v projektu. Slouží také jako kontejner pro spravované ovládací prvky, včetně hostitelských ovládacích prvků a model Windows Formsch ovládacích prvků, a uchovává informace o ovládacích prvcích na jeho povrchu. Další informace najdete v tématu [položka hostitele na listu](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Tato položka hostitele představuje sešit v projektu a slouží jako kontejner pro komponenty, které jsou sdíleny všemi listy v sešitu. Další informace najdete v tématu [položka hostitele sešitu](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Tato položka hostitele je list v aplikaci Excel, který obsahuje pouze graf a zpřístupňuje události.

     Když přidáte list grafu v době návrhu jako nový list v projektu systém Microsoft Office aplikace Excel pro přizpůsobení na úrovni dokumentu, aplikace Visual Studio automaticky vytvoří <xref:Microsoft.Office.Tools.Excel.ChartSheet> položku hostitele.

     I když je položka hostitelelistemvaplikaciExcel,nelzedolistugrafupřidatžádnéovládacíprvky.<xref:Microsoft.Office.Tools.Excel.ChartSheet> Chcete-li mít v listu s grafem jiné ovládací prvky, nepoužívejte list grafu. Místo toho můžete graf umístit jako vložený objekt na list pomocí <xref:Microsoft.Office.Tools.Excel.Chart> hostitelského ovládacího prvku. Další informace najdete v tématu [ovládací prvek grafu](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>hostitelské ovládací prvky aplikace Excel
 K dispozici je několik ovládacích prvků pro hostování v aplikaci Excel, které vám pomohou vytvořit, uspořádat a automatizovat sešity a listy. Tyto hostitelské ovládací prvky poskytují události a funkce vazby dat, které jejich protějšky v nativním objektovém modelu aplikace Excel nemají.

 Další informace o hostitelských ovládacích prvcích, které lze použít v projektech aplikace Excel, naleznete v následujících tématech:

- [Ovládací prvek grafu](../vsto/chart-control.md)

- [Ovládací prvek ListObject](../vsto/listobject-control.md)

- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)

- [Ovládací prvek XmlMappedRange –](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Viz také:
- [Postupy: Vyplnit ovládací prvky ListObject daty](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Postupy: Přidat ovládací prvky grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků XmlMappedRange – do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Postupy: Ověřit data při přidání nového řádku do ovládacího prvku ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Postupy: Mapování sloupců ListObject na data](../vsto/how-to-map-listobject-columns-to-data.md)
- [Návod: Program pro události ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
