---
title: řešení pro aplikaci Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 917a83a434dc27074b0d786f64fcdbdc5fd294d3
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027390"
---
# <a name="excel-solutions"></a>řešení pro aplikaci Excel
  Visual Studio obsahuje šablony projektů, které lze použít k vytvoření přizpůsobení na úrovni dokumentu a doplňky VSTO pro aplikaci Microsoft Office Excel. Tato řešení můžete použít k automatizaci aplikace Excel, rozšíření funkcí aplikace Excel a přizpůsobení uživatelského rozhraní (UI) aplikace Excel. Další informace o rozdílech mezi přizpůsobení na úrovni dokumentu a doplňky VSTO najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  

> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  

 Toto téma poskytuje následující informace:  

-   [Automatizace aplikace Excel](#automating).  

-   [Vývoj přizpůsobení na úrovni dokumentu pro Excel](#doclevel).  

-   [Vývoj doplňků VSTO pro Excel](#applevel).  

-   [Přizpůsobení uživatelského rozhraní aplikace Excel](#UI).  

##  <a name="automating"></a> Automatizace aplikace Excel  
 Model objektů aplikace Excel poskytuje mnoho typů, které můžete použít k automatizaci aplikace Excel. Například můžete programově vytvářet grafy, formátování listů a nastavte hodnoty rozsahů a buněk. Další informace najdete v tématu [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  

 Při vývoji řešení pro aplikaci Excel v sadě Visual Studio, můžete použít také *hostovat položky* a *hostování ovládacích prvků* ve vašich řešeních. Jedná se o objekty, které rozšiřují některé běžně používané objekty v objektovém modelu Excelu, jako <xref:Microsoft.Office.Interop.Excel.Worksheet> a <xref:Microsoft.Office.Interop.Excel.Range> objekty. Rozšířené objekty se chovají jako objekty aplikace Excel, které jsou založeny na, ale přidávají další události a možnosti vázání dat na objekty. Další informace najdete v tématu [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).  

##  <a name="doclevel"></a> Vývoj přizpůsobení na úrovni dokumentu pro Excel  
 Přizpůsobení úrovni dokumentu pro aplikaci Microsoft Office Excel se skládá ze sestavení, který je spojen s konkrétním sešitu. Sestavení obvykle rozšiřuje sešit přizpůsobením uživatelského rozhraní a automatizací aplikace Excel. Na rozdíl od doplňku VSTO, které je spojeno s Excelem, sama, funkce, kterou implementujete ve vlastním nastavení je k dispozici pouze v případě, že je přidružený sešit otevřít v aplikaci Excel.  

 Vytvoření projektu přizpůsobení na úrovni dokumentu pro Excel, použijte Excelový sešit nebo šablony projektů šablona aplikace Excel v **nový projekt** dialogové okno sady Visual Studio. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

 Další informace o úpravách na úrovni dokumentu naleznete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  

### <a name="excel-customization-programming-model"></a>Programovací model přizpůsobení aplikace Excel  
 Při vytváření projektu úrovni dokumentu pro Excel, sada Visual Studio generuje několik tříd, které jsou základem vašeho řešení: `ThisWorkbook`, `Sheet1`, `Sheet2`, a `Sheet3`. Tyto třídy představují sešit a listy, které jsou spojeny s řešením a poskytují výchozí bod pro psaní kódu.  

 Další informace o těchto generované třídy a další funkce můžete použít v projektu úrovni dokumentu naleznete v tématu [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  

##  <a name="applevel"></a> Vývoj doplňků VSTO pro Excel  
 Doplňku VSTO pro Microsoft Office Excelu obsahuje sestavení, který je načten v Excelu. Sestavení obvykle rozšiřuje aplikaci Excel, přizpůsobením uživatelského rozhraní a automatizací aplikace Excel. Na rozdíl od přizpůsobení úrovni dokumentu, který je přidružen konkrétní sešitu, není omezen na libovolný jednoho sešit funkce, kterou implementujete v doplňku VSTO.  

 Vytvoření projektu doplňku VSTO pro Excel, použijte Excelový sešit nebo šablony projektů šablona aplikace Excel v **nový projekt** dialogové okno sady Visual Studio. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

 Obecné informace o tom, jak fungují doplňků VSTO najdete v tématu [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>V programovacím modelu doplňku pro Excel  
 Při vytváření projektu doplňku VSTO pro Excel Visual Studio vygeneruje třídy, nazvané `ThisAddIn`, které jsou základem vašeho řešení. Tato třída poskytuje výchozí bod pro psaní kódu a také poskytuje objektový model aplikace Excel k doplňku VSTO.  

 Další informace o `ThisAddIn` třídy a dalšími funkcemi sady Visual Studio můžete použít v VSTO Add-in, naleznete v tématu [Program doplňků VSTO](../vsto/programming-vsto-add-ins.md).  

##  <a name="UI"></a> Přizpůsobení uživatelského rozhraní aplikace Excel  
 Existuje několik různých způsobů přizpůsobení uživatelského rozhraní aplikace Excel. Některé možnosti jsou dostupné pro všechny typy projektů a další možnosti jsou k dispozici pouze pro doplňky VSTO nebo přizpůsobení na úrovni dokumentu.  

### <a name="options-for-all-project-types"></a>Možnosti pro všechny typy projektů  
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici pro přizpůsobení na úrovni dokumentu a doplňky VSTO.  

|Úloha|Další informace|  
|----------|--------------------------|  
|Přizpůsobení pásu karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
|Přidání ovládacích prvků Windows Forms nebo rozšířené ovládací prvky aplikace Excel do listu v sešitu přizpůsobené pro přizpůsobení na úrovni dokumentu nebo v jakékoli otevřít sešit pro doplňku VSTO.|[Postupy: Přidání ovládacích prvků Windows forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků graf do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  

### <a name="options-for-document-level-customizations"></a>Možnosti pro přizpůsobení na úrovni dokumentu  
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici jenom pro přizpůsobení na úrovni dokumentu.  

|Úloha|Další informace|  
|----------|--------------------------|  
|Přidání podokna akcí do sešitu.|[Přehled podokna akcí](../vsto/actions-pane-overview.md)<br /><br /> [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Přidání ovládacích prvků rozšířenou rozsahu, které jsou mapovány na uzly XML do listu.|[Postupy: Přidání ovládacích prvků XMLMappedRange do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  

### <a name="options-for-vsto-add-ins"></a>Možnosti pro doplňky VSTO  
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici pouze pro doplňky VSTO.  

|Úloha|Další informace|  
|----------|--------------------------|  
|Vytvoření vlastního podokna úloh.|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|  

### <a name="related-topics"></a>Související témata  

| Název | Popis |
| - | - |
| [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md) | Obsahuje přehled hlavních typů poskytnutý objektovým modelem aplikace Excel. |
| [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md) | Poskytuje informace o rozšířených objektech (poskytovaných [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), který vám pomůže v řešení pro aplikaci Excel. |
| [Globalizace a lokalizace řešení pro Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Obsahuje informace o důležité informace pro řešení pro aplikaci Excel, které se spustí na počítačích, které mají jiné než anglické jazykové nastavení pro Windows. |
| [Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md) | Popisuje, jak přidat ovládací prvky Windows Forms na listech aplikace Excel. |
| [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Ukazuje, jak vytvořit základní přizpůsobení úrovni dokumentu pro Excel. |
| [Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Ukazuje, jak vytvořit základní Add-in VSTO pro Excel. |
| [Návod: Přidání ovládacích prvků na list za běhu v projektu doplňku VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Ukazuje, jak přidat tlačítko Windows Forms <xref:Microsoft.Office.Tools.Excel.NamedRange>a <xref:Microsoft.Office.Tools.Excel.ListObject> na list za běhu pomocí doplňku VSTO. |
| [Principy spoluvytváření a doplňků](./understanding-coauthoring-and-addins.md) | Popisuje úpravy, které možná budete muset provést tak, aby vyhovovaly spoluvytváření svá řešení. |
| [Excel 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199011) | Obsahuje odkazy na články a referenční dokumentaci o vývoji řešení pro aplikaci Excel. Ty nejsou specifická pro vývoj pro Office pomocí sady Visual Studio. |

