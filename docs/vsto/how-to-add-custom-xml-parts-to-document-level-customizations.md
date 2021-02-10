---
title: 'Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu'
description: Přečtěte si, jak můžete ukládat data XML do systém Microsoft Office excelový sešit nebo systém Microsoft Office wordový dokument vytvořením vlastní části XML v přizpůsobení na úrovni dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 11202da11cee72ec368ac525fce13fd084ab99be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954251"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu
  Data XML můžete ukládat do systém Microsoft Office excelového sešitu nebo systém Microsoft Office dokumentu aplikace Word vytvořením vlastní části XML v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio neposkytuje projekty na úrovni dokumentu pro systém Microsoft Office PowerPointu. Informace o přidání vlastní součásti XML do prezentace aplikace PowerPoint pomocí doplňku VSTO naleznete v tématu [How to: Add a Custom XML Parts to Documents in VSTO Add-in](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Přidání vlastní části XML do excelového sešitu

1. Přidá nový <xref:Microsoft.Office.Core.CustomXMLPart> objekt do <xref:Microsoft.Office.Core.CustomXMLParts> kolekce v sešitu. <xref:Microsoft.Office.Core.CustomXMLPart>Obsahuje řetězec XML, který chcete uložit do sešitu.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2. Přidejte `AddCustomXmlPartToWorkbook` metodu do `ThisWorkbook` třídy v projektu na úrovni dokumentu pro Excel.

3. Zavolejte metodu z jiného kódu v projektu. Chcete-li například vytvořit vlastní část XML, když uživatel otevře sešit, zavolejte metodu z `ThisWorkbook_Startup` obslužné rutiny události.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Přidání vlastní části XML do wordového dokumentu

1. Přidá nový <xref:Microsoft.Office.Core.CustomXMLPart> objekt do <xref:Microsoft.Office.Core.CustomXMLParts> kolekce v dokumentu. <xref:Microsoft.Office.Core.CustomXMLPart>Obsahuje řetězec XML, který chcete uložit v dokumentu.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2. Přidejte `AddCustomXmlPartToDocument` metodu do `ThisDocument` třídy v projektu na úrovni dokumentu pro aplikaci Word.

3. Zavolejte metodu z jiného kódu v projektu. Chcete-li například vytvořit vlastní část XML, když uživatel otevře dokument, zavolejte metodu z `ThisDocument_Startup` obslužné rutiny události.

## <a name="robust-programming"></a>Robustní programování
 Pro zjednodušení tento příklad používá řetězec XML, který je definován jako místní proměnná v metodě. Obvykle byste měli získat XML z externího zdroje, jako je například soubor nebo databáze.

## <a name="see-also"></a>Viz také
- [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md)
- [Postupy: Přidání vlastních částí XML do dokumentů pomocí doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
