---
title: řešení pro aplikaci Excel
description: Naučte se používat šablony projektů k automatizaci Excelu, rozšiřování funkcí Excelu a přizpůsobení uživatelského rozhraní (UI) Excelu.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3833ff549b2cceb3f783afc43a4f71dacc00ecb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931276"
---
# <a name="excel-solutions"></a>řešení pro aplikaci Excel
  Visual Studio poskytuje projektové šablony, které můžete použít k vytvoření přizpůsobení na úrovni dokumentu a doplňků VSTO pro systém Microsoft Office Excel. Tato řešení můžete použít k automatizaci aplikace Excel, rozšiřování funkcí aplikace Excel a přizpůsobení uživatelského rozhraní (UI) aplikace Excel. Další informace o rozdílech mezi přizpůsobením na úrovni dokumentu a doplňky VSTO najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Toto téma poskytuje následující informace:

- [Automatizujte Excel](#automating).

- [Vývoj přizpůsobení na úrovni dokumentu pro Excel](#doclevel)

- [Vývoj doplňků VSTO pro Excel](#applevel)

- [Přizpůsobení uživatelského rozhraní aplikace Excel](#UI).

## <a name="automate-excel"></a><a name="automating"></a> Automatizace Excelu
 Objektový model aplikace Excel zpřístupňuje mnoho typů, které lze použít k automatizaci aplikace Excel. Můžete například programově vytvářet grafy, formátovat listy a nastavovat hodnoty rozsahů a buněk. Další informace najdete v tématu [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

 Při vývoji řešení aplikace Excel v aplikaci Visual Studio můžete také použít *položky hostitele* a *hostitelské ovládací prvky* ve vašich řešeních. Jedná se o objekty, které rozšířily určité běžně používané objekty v objektovém modelu aplikace Excel, jako například <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> objekty a. Rozšířené objekty se chovají jako objekty aplikace Excel, na kterých jsou založeny, ale přidávají do objektů další události a funkce vazby dat. Další informace najdete v tématu [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> Vývoj přizpůsobení na úrovni dokumentu pro Excel
 Přizpůsobení na úrovni dokumentu pro systém Microsoft Office Excel se skládá ze sestavení, které je přidruženo ke konkrétnímu sešitu. Sestavení obvykle rozšiřuje sešit přizpůsobením uživatelského rozhraní a automatizací aplikace Excel. Na rozdíl od doplňku VSTO, který je přidružený k samotnému Excelu, je funkce, kterou implementujete v přizpůsobení, dostupná jenom v případě, že je přidružený sešit otevřený v Excelu.

 Chcete-li vytvořit projekt přizpůsobení na úrovni dokumentu pro aplikaci Excel, použijte šablony sešitu aplikace Excel nebo šablony projektů aplikace Excel v dialogovém okně **Nový projekt** aplikace Visual Studio. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Další informace o tom, jak přizpůsobení na úrovni dokumentu fungují, najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Programovací model přizpůsobení aplikace Excel
 Když vytvoříte projekt na úrovni dokumentu pro aplikaci Excel, aplikace Visual Studio vygeneruje několik tříd, které jsou základem vašeho řešení: `ThisWorkbook` , `Sheet1` , `Sheet2` a `Sheet3` . Tyto třídy představují sešit a listy, které jsou přidruženy k vašemu řešení, a poskytují výchozí bod pro psaní kódu.

 Další informace o těchto vygenerovaných třídách a dalších funkcích, které můžete použít v projektu na úrovni dokumentu, najdete v tématu [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> Vývoj doplňků VSTO pro Excel
 Doplněk VSTO pro systém Microsoft Office Excel se skládá ze sestavení načteného aplikací Excel. Sestavení obvykle rozšiřuje aplikaci Excel přizpůsobením uživatelského rozhraní a automatizací aplikace Excel. Na rozdíl od přizpůsobení na úrovni dokumentu, které je přidruženo k určitému sešitu, funkce, které implementujete v doplňku VSTO, nejsou omezeny pouze na jeden sešit.

 Chcete-li vytvořit projekt doplňku VSTO pro Excel, použijte excelový sešit nebo šablony projektů Excelu v dialogovém okně **Nový projekt** aplikace Visual Studio. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Obecné informace o tom, jak doplňky VSTO fungují, najdete v tématu [architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Programovací model doplňku aplikace Excel
 Když vytvoříte projekt doplňku VSTO pro Excel, aplikace Visual Studio vygeneruje třídu, `ThisAddIn` která je volána, což je základem vašeho řešení. Tato třída poskytuje výchozí bod pro psaní kódu a také zpřístupňuje objektový model Excelu do doplňku VSTO.

 Další informace o `ThisAddIn` třídě a dalších funkcích sady Visual Studio, které můžete použít v doplňku VSTO, najdete v tématu [Programová doplňky VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> Přizpůsobení uživatelského rozhraní Excelu
 Existuje několik různých způsobů, jak přizpůsobit uživatelské rozhraní aplikace Excel. Některé možnosti jsou k dispozici pro všechny typy projektů a další možnosti jsou k dispozici pouze pro doplňky VSTO nebo přizpůsobení na úrovni dokumentu.

### <a name="options-for-all-project-types"></a>Možnosti pro všechny typy projektů
 V následující tabulce jsou uvedeny možnosti přizpůsobení, které jsou k dispozici pro přizpůsobení na úrovni dokumentu a doplňky VSTO.

|Úkol|Další informace|
|----------|--------------------------|
|Přizpůsobení pásu karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|
|Přidejte model Windows Forms ovládací prvky nebo rozšířené ovládací prvky aplikace Excel do listu v přizpůsobeném sešitu pro přizpůsobení na úrovni dokumentu nebo v jakémkoli otevřeném sešitu doplňku VSTO.|[Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Možnosti pro přizpůsobení na úrovni dokumentu
 V následující tabulce jsou uvedeny možnosti přizpůsobení, které jsou k dispozici pouze pro přizpůsobení na úrovni dokumentu.

|Úkol|Další informace|
|----------|--------------------------|
|Přidejte podokno akcí do sešitu.|[Přehled podokna akcí](../vsto/actions-pane-overview.md)<br /><br /> [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Přidejte rozšířené ovládací prvky rozsahu, které jsou namapovány na uzly XML na list.|[Postupy: Přidání ovládacích prvků XmlMappedRange – do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Možnosti doplňků VSTO
 V následující tabulce jsou uvedeny možnosti přizpůsobení, které jsou k dispozici pouze pro doplňky VSTO.

|Úkol|Další informace|
|----------|--------------------------|
|Vytvoří vlastní podokno úloh.|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Související témata

| Nadpis | Popis |
| - | - |
| [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md) | Poskytuje přehled hlavních typů poskytovaných modelem objektu aplikace Excel. |
| [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md) | Poskytuje informace o rozšířených objektech (poskytovaných [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ), které můžete použít v řešeních aplikace Excel. |
| [Globalizace a lokalizace řešení pro Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Obsahuje informace o speciálních faktorech pro řešení aplikace Excel, které se spustí v počítačích, které mají nastavení jiné než anglické verze systému Windows. |
| [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md) | Popisuje, jak lze přidat ovládací prvky model Windows Forms do listů aplikace Excel. |
| [Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Ukazuje, jak vytvořit základní přizpůsobení na úrovni dokumentu pro aplikaci Excel. |
| [Návod: vytvoření prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Ukazuje, jak vytvořit základní doplněk VSTO pro Excel. |
| [Návod: Přidání ovládacích prvků na list v době běhu v projektu doplňku VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Ukazuje, jak přidat model Windows Forms tlačítko, <xref:Microsoft.Office.Tools.Excel.NamedRange> a a <xref:Microsoft.Office.Tools.Excel.ListObject> do listu za běhu pomocí doplňku VSTO. |
| [Principy společného vytváření a doplňků](./understanding-coauthoring-and-addins.md) | Popisuje úpravy, které možná budete muset udělat pro vaše řešení, abyste mohli přizpůsobit spoluvytváření. |
| [Excel 2010 ve vývoji pro Office](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Obsahuje odkazy na články a referenční dokumentaci týkající se vývoje řešení v aplikaci Excel. Tyto aplikace nejsou specifické pro vývoj pro Office pomocí sady Visual Studio. |
