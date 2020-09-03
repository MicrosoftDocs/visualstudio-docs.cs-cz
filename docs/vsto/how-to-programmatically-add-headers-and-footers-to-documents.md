---
title: 'Postupy: přidávání hlaviček a zápatí do dokumentů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52724103df17a1eaaf364f255f127a576beda798
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519922"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Postupy: přidávání hlaviček a zápatí do dokumentů prostřednictvím kódu programu
  Do hlaviček a zápatí v dokumentu můžete přidat text pomocí <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> vlastnosti a <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Section> . Každý oddíl dokumentu obsahuje tři záhlaví a zápatí:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Postupy se liší pro přizpůsobení na úrovni dokumentu a doplňky VSTO.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Přizpůsobení na úrovni dokumentu
 Chcete-li použít následující příklady kódu, spusťte je z `ThisDocument` třídy v projektu.

### <a name="to-add-text-to-footers-in-the-document"></a>Přidání textu do zápatí v dokumentu

1. Následující příklad kódu nastaví písmo textu, který má být vložen do primárního zápatí každého oddílu dokumentu, a poté vloží text do zápatí.

     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Přidání textu do záhlaví v dokumentu

1. Následující příklad kódu přidá pole pro zobrazení čísla stránky v jednotlivých hlavičkách v dokumentu a pak nastaví zarovnání odstavce tak, aby text byl zarovnán napravo od záhlaví.

     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]

## <a name="vsto-add-ins"></a>Doplňky VSTO
 Chcete-li použít následující příklady kódu, spusťte je z `ThisAddIn` třídy v projektu.

### <a name="to-add-text-to-footers-in-a-document"></a>Přidání textu do zápatí v dokumentu

1. Následující příklad kódu nastaví písmo textu, který má být vložen do primárního zápatí každého oddílu dokumentu, a poté vloží text do zápatí. Tento příklad kódu používá aktivní dokument.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Přidání textu do záhlaví v dokumentu

1. Následující příklad kódu přidá pole pro zobrazení čísla stránky v jednotlivých hlavičkách v dokumentu a pak nastaví zarovnání odstavce tak, aby text byl zarovnán napravo od záhlaví. Tento příklad kódu používá aktivní dokument.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]

## <a name="see-also"></a>Viz také
- [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
