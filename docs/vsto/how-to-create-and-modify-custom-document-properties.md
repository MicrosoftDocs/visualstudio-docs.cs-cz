---
title: 'Postupy: vytváření a změny přizpůsobených vlastností dokumentu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb66d2fbd1af41cfa89fc38f7694ee3783d10f76
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254433"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Postupy: vytváření a změny přizpůsobených vlastností dokumentu
  Aplikace Microsoft Office, které jsou uvedené výše zadejte předdefinované vlastnosti, které jsou uloženy s dokumenty. Kromě toho můžete vytvořit a upravit vlastní vlastnosti dokumentu, pokud nejsou další informace, které chcete k uložení dokumentu v platnosti.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Použijte vlastnost CustomDocumentProperties dokumentu pro práci s vlastní vlastnosti. Například v projektu úrovni dokumentu pro aplikaci Microsoft Office Excel použít <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> vlastnost `ThisWorkbook` třídy. V doplňku VSTO projektu pro aplikaci Excel, pomocí <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Workbook> objektu. Tyto vlastnosti vrátit <xref:Microsoft.Office.Core.DocumentProperties> objekt, který je kolekce z <xref:Microsoft.Office.Core.DocumentProperty> objekty. Můžete použít `Item` vlastnosti kolekce pro načtení určité vlastnosti, pomocí názvu nebo podle indexu v kolekci.  
  
 Následující příklad ukazuje, jak přidat vlastní vlastnosti v přizpůsobení na úrovni dokumentu pro Excel a přiřaďte ho hodnotu.  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související Videoukázka, najdete v části [jak I: přístup a manipulaci s vlastní vlastnosti dokumentu v Microsoft Wordu?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Příklad  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Při pokusu o přístup `Value` vlastnost pro nedefinované vlastnosti vyvolá výjimku.  
  
## <a name="see-also"></a>Viz také:  
 [Program doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Úpravy na úrovni dokumentů programu](../vsto/programming-document-level-customizations.md)   
 [Postupy: čtení z a zápis do vlastností dokumentu](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  