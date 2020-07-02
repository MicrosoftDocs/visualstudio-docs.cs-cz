---
title: 'Postupy: čtení z vlastností dokumentu a zápis do nich'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: adad9ec70290f426ce7c3c59ad13ff8636a69463
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541320"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Postupy: čtení z vlastností dokumentu a zápis do nich
  Můžete uložit vlastnosti dokumentu spolu s dokumentem. Aplikace Office poskytují řadu předdefinovaných vlastností, jako je například autor, název a předmět. V tomto tématu se dozvíte, jak nastavit vlastnosti dokumentu v systém Microsoft Office Excelu a systém Microsoft Office Wordu.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Nastavení vlastností dokumentu v Excelu
 Chcete-li pracovat s integrovanými vlastnostmi v aplikaci Excel, použijte následující vlastnosti:

- V projektu na úrovni dokumentu použijte <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> vlastnost `ThisWorkbook` třídy.

- V projektu doplňku VSTO použijte <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Workbook> objektu.

  Tyto vlastnosti vrátí <xref:Microsoft.Office.Core.DocumentProperties> objekt, který je kolekcí <xref:Microsoft.Office.Core.DocumentProperty> objektů. Můžete použít `Item` vlastnost kolekce k načtení konkrétní vlastnosti, buď podle názvu, nebo podle indexu v rámci kolekce.

  Následující příklad kódu ukazuje, jak změnit vlastnost předdefinované **číslo revize** v projektu na úrovni dokumentu.

### <a name="to-change-the-revision-number-property-in-excel"></a>Změna vlastnosti číslo revize v aplikaci Excel

1. Přiřaďte k proměnné předdefinované vlastnosti dokumentu.

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. Zvyšte `Revision Number` vlastnost o jednu.

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>Nastavení vlastností dokumentu ve Wordu
 Chcete-li ve Wordu pracovat s vestavěnými vlastnostmi, použijte následující vlastnosti:

- V projektu na úrovni dokumentu použijte <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> vlastnost `ThisDocument` třídy.

- V projektu doplňku VSTO použijte <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Document> objektu.

  Tyto vlastnosti vrátí <xref:Microsoft.Office.Core.DocumentProperties> objekt, který je kolekcí <xref:Microsoft.Office.Core.DocumentProperty> objektů. Můžete použít `Item` vlastnost kolekce k načtení konkrétní vlastnosti, buď podle názvu, nebo podle indexu v rámci kolekce.

  Následující příklad kódu ukazuje, jak změnit integrovanou vlastnost **Subject** v projektu na úrovni dokumentu.

### <a name="to-change-the-subject-property"></a>Změna vlastnosti Subject

1. Přiřaďte k proměnné předdefinované vlastnosti dokumentu.

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. Změňte `Subject` vlastnost na dokument White Paper.

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>Robustní programování
 V příkladech se předpokládá, že jste napsali kód ve `ThisWorkbook` třídě v projektu na úrovni dokumentu pro aplikaci Excel a `ThisDocument` třídu v projektu na úrovni dokumentu pro aplikaci Word.

 I když pracujete s Wordem a Excelu a jejich objekty, systém Microsoft Office poskytuje seznam dostupných vlastností dokumentu. Pokus o přístup k nedefinované vlastnosti vyvolá výjimku.

## <a name="see-also"></a>Viz také:
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Postupy: vytváření a úpravy vlastností vlastního dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)
