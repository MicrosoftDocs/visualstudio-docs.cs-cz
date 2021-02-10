---
title: Vlastnosti v projektech pro systém Office
description: Přečtěte si informace o vlastnostech, které jsou k dispozici pro projekty Office v sadě Visual Studio, prostřednictvím okno Vlastnosti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f7a2ab04e1926a53c3d3aa05023103206c6aa01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971762"
---
# <a name="properties-in-office-projects"></a>Vlastnosti v projektech pro systém Office
  Existuje několik důležitých vlastností, které jsou k dispozici pro projekty Office v sadě Visual Studio. Tyto vlastnosti jsou k dispozici v okně **vlastnosti** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Obor názvů pro hostitelskou položku
 Pomocí **oboru názvů pro vlastnost položky hostitele** změňte obor názvů pro třídy položek hostitele (například `ThisAddIn` `ThisWorkbook` třídy, nebo `ThisDocument` ) v projektech Visual C#. Tato vlastnost se zobrazí v okně **vlastnosti** při výběru uzlu dokumentu v projektu na úrovni dokumentu (například *ExcelWorkbook1.xlsx* nebo *WordDocument1.docx*) nebo uzlu aplikace v projektu doplňku VSTO (například Excel nebo Word) v **Průzkumník řešení**.

 Při vytváření projektu sady Visual C# pro sadu se položkám hostitelů předává obor názvů na základě názvu projektu. Doporučuje se použít vlastnost **Namespace pro hostitelskou položku** pro změnu oboru názvů místo přímé úpravy souborů kódu. Použijete-li tuto vlastnost, obor názvů se změní ve vygenerovaném (skrytém) souboru kódu a také v zobrazených souborech kódu.

## <a name="cacheindocument"></a>CacheInDocument
 Vlastnost **CacheInDocument** se zobrazí v okně **vlastnosti** pro projekty na úrovni dokumentu při výběru instance <xref:System.Data.DataSet> v návrháři aplikace Visual Studio. Do mezipaměti lze ukládat pouze veřejné členy. Ujistěte se, že vlastnost **modifikátory** je nastavena na hodnotu **Public** , pokud chcete uložit do mezipaměti <xref:System.Data.DataSet> .

 Tato vlastnost přebírá logickou hodnotu:

- Pokud chcete datovou sadu v dokumentu ukládat do mezipaměti, vyberte **true** .

- Pokud nechcete, aby byla datová sada ukládána do mezipaměti v dokumentu, vyberte **hodnotu false** .

  Další informace o ukládání dat do mezipaměti najdete [v tématu data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Argument
 Vlastnost **hodnota2** je k dispozici pouze pro excelový sešit nebo šablony projektů. Zobrazuje se pod uzlem vlastnosti **DataBindings** v okně **vlastnosti** při výběru <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku v Návrháři listů.

 Vlastnost **hodnota2** v okně **vlastnosti** použijte k navázání <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnosti <xref:Microsoft.Office.Tools.Excel.NamedRange> na pole ve zdroji dat.

## <a name="see-also"></a>Viz také
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
- [Události v projektech pro systém Office](../vsto/events-in-office-projects.md)
