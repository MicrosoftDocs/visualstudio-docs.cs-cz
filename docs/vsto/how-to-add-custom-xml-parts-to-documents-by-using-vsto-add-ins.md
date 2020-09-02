---
title: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92c00ea69069b7374f5f595cc6f198aac23d1f91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538291"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Postupy: Přidání vlastních částí XML do dokumentů pomocí doplňků VSTO
  Data XML můžete ukládat do následujících typů dokumentů vytvořením vlastní části XML v doplňku VSTO:

- Systém Microsoft Office excelový sešit.

- Systém Microsoft Office wordový dokument.

- Prezentace aplikace systém Microsoft Office PowerPoint.

  Další informace najdete v tématu [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md).

  **Platí pro:** Informace v tomto tématu se vztahují na projekty na úrovni aplikace v Excelu, PowerPointu a Wordu. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Přidání vlastní části XML do excelového sešitu

1. Přidá nový <xref:Microsoft.Office.Core.CustomXMLPart> objekt do <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> kolekce v sešitu. <xref:Microsoft.Office.Core.CustomXMLPart>Obsahuje řetězec XML, který chcete uložit do sešitu.

     Následující příklad kódu přidá vlastní část XML do zadaného sešitu.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. Přidejte `AddCustomXmlPartToWorkbook` metodu do `ThisAddIn` třídy v projektu doplňku VSTO pro Excel.

3. Zavolejte metodu z jiného kódu v projektu. Chcete-li například vytvořit vlastní část XML, když uživatel otevře sešit, zavolejte metodu z obslužné rutiny události pro <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> událost.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Přidání vlastní části XML do wordového dokumentu

1. Přidá nový <xref:Microsoft.Office.Core.CustomXMLPart> objekt do <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> kolekce v dokumentu. <xref:Microsoft.Office.Core.CustomXMLPart>Obsahuje řetězec XML, který chcete uložit v dokumentu.

     Následující příklad kódu přidá vlastní část XML do zadaného dokumentu.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. Přidejte `AddCustomXmlPartToDocument` metodu do `ThisAddIn` třídy v projektu doplňku VSTO pro Word.

3. Zavolejte metodu z jiného kódu v projektu. Chcete-li například vytvořit vlastní část XML, když uživatel otevře dokument, zavolejte metodu z obslužné rutiny události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> událost.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Přidání vlastní součásti XML do prezentace aplikace PowerPoint

1. Přidejte nový <xref:Microsoft.Office.Core.CustomXMLPart> objekt do kolekce [Microsoft. Office. Interop. PowerPoint. _Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) v prezentaci. <xref:Microsoft.Office.Core.CustomXMLPart>Obsahuje řetězec XML, který chcete uložit do prezentace.

     Následující příklad kódu přidá vlastní část XML do zadané prezentace.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. Přidejte `AddCustomXmlPartToPresentation` metodu do `ThisAddIn` třídy v projektu doplňku VSTO pro PowerPoint.

3. Zavolejte metodu z jiného kódu v projektu. Chcete-li například vytvořit vlastní část XML, když uživatel otevře prezentaci, zavolejte metodu z obslužné rutiny události pro událost [Microsoft. Office. Interop. PowerPoint. EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) .

## <a name="robust-programming"></a>Robustní programování
 Pro zjednodušení tento příklad používá řetězec XML, který je definován jako místní proměnná v metodě. Obvykle byste měli získat XML z externího zdroje, jako je například soubor nebo databáze.

## <a name="see-also"></a>Viz také
- [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md)
- [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
