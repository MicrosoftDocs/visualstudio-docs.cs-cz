---
title: Programové omezení hostitelských položek a hostitelských ovládacích prvků
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 97b94291a3fd057e82bd79aa4f6c3220020bc24a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255804"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Programové omezení hostitelských položek a hostitelských ovládacích prvků
  Každá položka hostitele a řízení hostitele je navržena tak, aby se chovala jako odpovídající nativní objekt systém Microsoft Office Word nebo systém Microsoft Office Excel s dalšími funkcemi. Existují však některé zásadní rozdíly mezi chováním hostitelských položek a hostitelských ovládacích prvků a nativních objektů Office v době běhu.

 Obecné informace o hostitelských položkách a hostitelských ovládacích prvcích najdete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Programové vytváření hostitelských položek
 Když programově vytvoříte nebo otevřete dokument, sešit nebo sešit za běhu pomocí objektového modelu Word nebo Excel, položka není položkou hostitele. Místo toho je nový objekt nativním objektem Office. Například pokud použijete <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodu k vytvoření nového dokumentu aplikace Word v době běhu, bude to <xref:Microsoft.Office.Interop.Word.Document> spíše nativní objekt než <xref:Microsoft.Office.Tools.Word.Document> Hostitelská položka. Podobně když vytvoříte nový list v době běhu pomocí <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody, získáte nativní <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt spíše než <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelskou položku.

 V projektech na úrovni dokumentu nelze v době běhu vytvořit položky hostitele. Hostitelské položky lze vytvořit pouze v době návrhu v projektech na úrovni dokumentu. Další informace naleznete v části položka [hostitele dokumentu](../vsto/document-host-item.md), [položka hostitele sešitu](../vsto/workbook-host-item.md)a [položka hostitele listu](../vsto/worksheet-host-item.md).

 V projektech doplňku VSTO můžete v <xref:Microsoft.Office.Tools.Word.Document> době běhu vytvořit, <xref:Microsoft.Office.Tools.Excel.Workbook> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet> hostovat položky. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Programové vytváření hostitelských ovládacích prvků
 V době běhu můžete programově přidat hostitelské ovládací prvky do <xref:Microsoft.Office.Tools.Word.Document> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet> položky hostitele. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Nemůžete přidat hostitelské ovládací prvky do nativního <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Worksheet> .

> [!NOTE]
> Následující hostitelské ovládací prvky nelze programově přidat do listů ani dokumentů: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> a <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Pochopení rozdílů mezi typy hostitelských položek, hostitelských ovládacích prvků a nativních objektů Office
 Pro každou hostitelskou položku a hostitelský ovládací prvek je k dispozici základní nativní systém Microsoft Office Word nebo systém Microsoft Office excelový objekt. K základnímu objektu můžete přistupovat pomocí vlastnosti InnerObject položky hostitele nebo hostitelského ovládacího prvku. Neexistuje však způsob, jak přetypovat objekt nativního systému Office na jeho odpovídající položku hostitele nebo hostitelský ovládací prvek. Pokud se pokusíte přetypovat objekt nativní sady Office na typ hostitelské položky nebo hostitelského ovládacího prvku, <xref:System.InvalidCastException> je vyvolána výjimka.

 Existuje několik scénářů, kdy rozdíly mezi typy hostitelských položek a hostitelských ovládacích prvků a podkladových nativních objektů Office mohou ovlivnit váš kód.

### <a name="pass-host-controls-to-methods-and-properties"></a>Předání hostitelských ovládacích prvků metodám a vlastnostem
 V aplikaci Word nelze předat hostitelskému ovládacímu prvku metodu nebo vlastnost, která vyžaduje jako parametr nativní objekt aplikace Word. Pro návrat základního nativního objektu aplikace Word je nutné použít vlastnost InnerObject hostitelského ovládacího prvku. Například můžete předat <xref:Microsoft.Office.Interop.Word.Bookmark> objekt metodě předáním <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark> hostitelského ovládacího prvku do metody.

 V aplikaci Excel je nutné použít vlastnost InnerObject hostitelského ovládacího prvku k předání ovládacího prvku hostitele do metody nebo vlastnosti, pokud metoda nebo vlastnost očekává základní objekt aplikace Excel.

 Následující příklad vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek a předá ho <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodě. Kód používá <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> vlastnost pojmenovaného rozsahu pro vrácení základní kanceláře <xref:Microsoft.Office.Interop.Excel.Range> , která je vyžadována <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodou.

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Návratové typy nativních metod a vlastností Office
 Většina metod a vlastností položek hostitele vrátí základní nativní objekt Office, na kterém je založena Hostitelská položka. Například <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.NamedRange> hostitelského ovládacího prvku v aplikaci Excel vrátí <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt, nikoli <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelskou položku. Podobně <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> vlastnost <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hostitelského ovládacího prvku v aplikaci Word vrátí objekt, <xref:Microsoft.Office.Interop.Word.Document> nikoli <xref:Microsoft.Office.Tools.Word.Document> hostitelskou položku.

### <a name="access-collections-of-host-controls"></a>Přístup ke kolekcím hostitelských ovládacích prvků
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Neposkytuje jednotlivé kolekce pro každý typ hostitelského ovládacího prvku. Místo toho použijte vlastnost Controls položky hostitele k iterování přes všechny spravované ovládací prvky (ovládací prvky hostitele a model Windows Forms ovládací prvky) v dokumentu nebo listu a pak hledejte položky, které odpovídají typu hostitelského ovládacího prvku, který vás zajímá. Následující příklad kódu prověřuje každý ovládací prvek v dokumentu aplikace Word a určí, zda je ovládací prvek <xref:Microsoft.Office.Tools.Word.Bookmark> .

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Další informace o vlastnosti ovládacích prvků hostitelů naleznete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Objektové modely aplikace Word a Excel obsahují vlastnosti, které zpřístupňují kolekce nativních ovládacích prvků na dokumentech a listech. Pomocí těchto vlastností nelze přistupovat ke spravovaným ovládacím prvkům. Například není možné vytvořit výčet jednotlivých <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků hostitele v dokumentu pomocí <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Document> . Tyto vlastnosti obsahují pouze <xref:Microsoft.Office.Interop.Word.Bookmark> ovládací prvky v dokumentu. neobsahují <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky hostitele v dokumentu.

## <a name="see-also"></a>Viz také
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Položka hostitele sešitu](../vsto/workbook-host-item.md)
- [Položka hostitele dokumentu](../vsto/document-host-item.md)
