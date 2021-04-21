---
title: 'Postupy: vytváření a úpravy vlastností vlastního dokumentu'
description: Přečtěte si, jak můžete vytvořit a upravit vlastnosti vlastního dokumentu, pokud jsou k dokumentu k dispozici další informace, které chcete uložit.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd89cb1e2991f48fefd9984eaa6d5894d9b506c1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826574"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Postupy: vytváření a úpravy vlastností vlastního dokumentu
  Výše uvedené aplikace systém Microsoft Office poskytují předdefinované vlastnosti, které jsou uložené s dokumenty. Kromě toho můžete vytvořit a upravit vlastnosti vlastního dokumentu, pokud jsou k dokumentu k dispozici další informace, které chcete uložit.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Pro práci s vlastními vlastnostmi použijte vlastnost CustomDocumentProperties dokumentu. Například v projektu na úrovni dokumentu pro systém Microsoft Office Excel, použijte <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> vlastnost `ThisWorkbook` třídy. V projektu doplňku VSTO pro Excel použijte <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Workbook> objektu. Tyto vlastnosti vrátí <xref:Microsoft.Office.Core.DocumentProperties> objekt, který je kolekcí <xref:Microsoft.Office.Core.DocumentProperty> objektů. Můžete použít `Item` vlastnost kolekce k načtení konkrétní vlastnosti, buď podle názvu, nebo podle indexu v rámci kolekce.

 Následující příklad ukazuje, jak přidat vlastní vlastnost v přizpůsobení na úrovni dokumentu pro aplikaci Excel a přiřadit ji k hodnotě.

## <a name="example"></a>Příklad
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet6":::

## <a name="robust-programming"></a>Robustní programování
 Pokus o přístup k `Value` vlastnosti nedefinovaných vlastností vyvolá výjimku.

## <a name="see-also"></a>Viz také
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Postupy: čtení z vlastností dokumentu a zápis do nich](../vsto/how-to-read-from-and-write-to-document-properties.md)
