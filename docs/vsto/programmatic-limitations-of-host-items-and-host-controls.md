---
title: Programová omezení hostitelských položek a hostitelských ovládacích prvků
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0b7e45ed9ba8e9fcd42d57a1cc6aaf34ce3e3711
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693380"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Programová omezení hostitelských položek a hostitelských ovládacích prvků
  Jednotlivé položky hostitele a řízení hostitele je určena pro chovat jako odpovídající nativní aplikace Microsoft Office Word nebo objekt aplikace Microsoft Office Excel s dalšími funkcemi. Existují však určité základní rozdíly mezi chování hostitelských položek a hostitelských ovládacích prvků a nativní objektů Office za běhu.  
  
 Obecné informace o hostitelských položek a hostitelských ovládacích prvků najdete v tématu [hostitele položky a hostitelem Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>Hostitelské položky vytváření prostřednictvím kódu programu  
 Když prostřednictvím kódu programu vytvořit nebo otevřít dokument, sešit nebo list za běhu pomocí objektového modelu Word či Excel, položka není položku hostitele. Místo toho tento nový objekt je objekt nativní Office. Například pokud použijete <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodu pro vytvoření nového dokumentu aplikace Word v běh, bude nativní <xref:Microsoft.Office.Interop.Word.Document> objekt ne <xref:Microsoft.Office.Tools.Word.Document> hostitelská položka. Podobně platí, když vytvoříte nový list za běhu pomocí <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody get nativní <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt ne <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka.  
  
 V projektech na úrovni dokumentu nelze vytvořit hostitele položky v době běhu. Hostitelské položky lze vytvořit pouze v době návrhu v projekty na úrovni dokumentu. Další informace najdete v tématu [hostitelská položka Document](../vsto/document-host-item.md), [hostitelská položka Workbook](../vsto/workbook-host-item.md), a [hostitelská položka Worksheet](../vsto/worksheet-host-item.md).  
  
 Na projekty doplňku VSTO, můžete vytvořit <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, nebo <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitele položky v době běhu. Další informace najdete v tématu [dokumentů rozšířit aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-create-host-controls"></a>Hostitelské ovládací prvky vytváření prostřednictvím kódu programu  
 Hostitelské ovládací prvky pro můžete přidat prostřednictvím kódu programu <xref:Microsoft.Office.Tools.Word.Document> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka za běhu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Hostitelské ovládací prvky nelze přidat do nativní <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
> [!NOTE]  
>  Následující hostitelské ovládací prvky nelze přidat prostřednictvím kódu programu do listů nebo dokumenty: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, a <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Pochopit typ rozdíly mezi hostitelských položek, hostitelské ovládací prvky a nativní objektů Office  
 Pro každou položku hostitele a hostitelského ovládacího prvku je základní objekt nativní aplikace Microsoft Office Word nebo Microsoft Office Excel. Základní objekt můžete přistupovat pomocí vlastnosti InnerObject položky hostitele nebo hostitelského ovládacího prvku. Neexistuje však žádný způsob, jak převést objekt nativní Office na jeho odpovídající hostitelská položka nebo hostitelského ovládacího prvku. Pokud se pokusíte převést objekt nativní Office do typu položky hostitele nebo hostitelského ovládacího prvku, <xref:System.InvalidCastException> je vyvolána výjimka.  
  
 Existuje několik situací, kdy rozdíly mezi typy hostitelských položek a hostitelských ovládacích prvků a základní nativních objektů Office může ovlivnit váš kód.  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>Hostitelské ovládací prvky předat metod a vlastností  
 V aplikaci Word nemůžete předat hostitelského ovládacího prvku metody nebo vlastnosti, která vyžaduje objektu nativní aplikace Word jako parametr. Vlastnost InnerObject hostitelského ovládacího prvku používaly vrátí základní objekt nativní aplikace Word. Například můžete předat <xref:Microsoft.Office.Interop.Word.Bookmark> objekt, který má metoda předáním <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> vlastnost <xref:Microsoft.Office.Tools.Word.Bookmark> hostování ovládacího prvku metodě.  
  
 V aplikaci Excel musíte použít vlastnost InnerObject z hostitelského ovládacího prvku předat řízení hostitele metody nebo vlastnosti při metody nebo vlastnosti očekává základní objekt aplikace Excel.  
  
 Následující příklad vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> řízení a předává jej do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metoda. Kód používá <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> vlastnost s názvem rozsahu vrátit základní Office <xref:Microsoft.Office.Interop.Excel.Range> potřebuje <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metoda.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Návratové typy nativní Office metod a vlastností  
 Většina metody a vlastnosti hostitele položek vrátí základní nativní objekt Office, na kterém je hostitelská položka založena. Například <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.NamedRange> hostování ovládacího prvku v aplikaci Excel vrátí <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt ne <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka. Podobně <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> vlastnost <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hostování ovládacího prvku vrátí aplikace Word <xref:Microsoft.Office.Interop.Word.Document> objekt ne <xref:Microsoft.Office.Tools.Word.Document> hostitelská položka.  
  
### <a name="access-collections-of-host-controls"></a>Přístup ke kolekcím hostitelské ovládací prvky  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Neposkytuje jednotlivé kolekce pro každý typ hostitelského ovládacího prvku. Místo toho použijte vlastnost ovládací prvky položky hostitele k iteraci v rámci všech spravovaných ovládacích prvků (hostitelské ovládací prvky a ovládací prvky Windows Forms) v dokumentu nebo listu a potom vyhledejte položky, které odpovídají typu ovládacího prvku hostitele, které vás zajímají. Následující příklad kódu prozkoumá každý ovládací prvek na dokument aplikace Word a určuje, zda je ovládací prvek <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Další informace o vlastnosti ovládacích prvků hostitele položek najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Objektové modely Word a Excel obsahovat vlastnosti, které zveřejňují kolekce nativní ovládací prvky na dokumenty a listů. Spravované ovládací prvky nemáte přístup pomocí těchto vlastností. Například není možné vyjmenovat každý <xref:Microsoft.Office.Tools.Word.Bookmark> hostování ovládacího prvku v dokumentu s použitím <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> vlastnost <xref:Microsoft.Office.Tools.Word.Document>. Tyto vlastnosti obsahovat pouze <xref:Microsoft.Office.Interop.Word.Bookmark> ovládací prvky v dokumentu; neobsahují <xref:Microsoft.Office.Tools.Word.Bookmark> hostování ovládacích prvků v dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Hostitelská položka Worksheet](../vsto/worksheet-host-item.md)   
 [Hostitelská položka Workbook](../vsto/workbook-host-item.md)   
 [Hostitelská položka Document](../vsto/document-host-item.md)  
  
  