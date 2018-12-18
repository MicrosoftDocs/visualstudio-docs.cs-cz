---
title: 'Postupy: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a559f8c074a7e80ea898f86dc205dec6ad2bb064
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826893"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Postupy: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO
  XML data můžete ukládat následující typy dokumentů tak, že vytvoříte vlastní část XML v doplňku VSTO:  
  
- Sešit Microsoft Office Excel.  
  
- Dokument aplikace Microsoft Office Word.  
  
- Aplikace Microsoft Office PowerPoint.  
  
  Další informace najdete v tématu [přehled částí XML vlastní](../vsto/custom-xml-parts-overview.md).  
  
  **Platí pro:** informace v tomto tématu se vztahují na projekty na úrovni aplikace Excel, PowerPoint a Word. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Chcete-li přidat vlastní část XML k Excelovému sešitu  
  
1.  Přidat nový <xref:Microsoft.Office.Core.CustomXMLPart> objektu <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> kolekce v sešitu. <xref:Microsoft.Office.Core.CustomXMLPart> Obsahuje řetězec XML, který chcete uložit v sešitu.  
  
     Následující příklad kódu přidá vlastní část XML do zadaného sešitu.  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Přidat `AddCustomXmlPartToWorkbook` metodu `ThisAddIn` třídy v projektu doplňku VSTO pro Excel.  
  
3.  Volejte metodu od jiného kódu ve vašem projektu. Například pokud chcete vytvořit vlastní část XML, když uživatel otevře sešit, zavolejte metodu z obslužné rutiny události pro <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> událostí.  
  
## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Chcete-li přidat vlastní část XML do Wordového dokumentu  
  
1.  Přidat nový <xref:Microsoft.Office.Core.CustomXMLPart> objektu <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> kolekce v dokumentu. <xref:Microsoft.Office.Core.CustomXMLPart> Obsahuje řetězec XML, který chcete uložit v dokumentu.  
  
     Následující příklad kódu přidá vlastní část XML do zadaného dokumentu.  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Přidat `AddCustomXmlPartToDocument` metodu `ThisAddIn` třídy v projektu doplňku VSTO pro Word.  
  
3.  Volejte metodu od jiného kódu ve vašem projektu. Například pokud chcete vytvořit vlastní část XML, když uživatel otevře dokument, zavolejte metodu z obslužné rutiny události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> událostí.  
  
## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Přidání vlastních částí XML do Powerpointovou prezentaci.  
  
1.  Přidat nový <xref:Microsoft.Office.Core.CustomXMLPart> objektu [Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) kolekce v prezentaci. <xref:Microsoft.Office.Core.CustomXMLPart> Obsahuje řetězec XML, který chcete uložit v prezentaci.  
  
     Následující příklad kódu přidá vlastní část XML do zadaného prezentace.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  Přidat `AddCustomXmlPartToPresentation` metodu `ThisAddIn` třídy v projektu doplňku VSTO pro PowerPoint.  
  
3.  Volejte metodu od jiného kódu ve vašem projektu. Například pokud chcete vytvořit vlastní část XML, když uživatel otevře prezentace, zavolejte metodu z obslužné rutiny události pro [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) událostí.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro zjednodušení tento příklad používá řetězec jazyka XML, který je definován jako místní proměnná v metodě. Obvykle byste měli získat XML z externího zdroje, jako je například soubor nebo databáze.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md)   
 [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  