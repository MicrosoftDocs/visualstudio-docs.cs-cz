---
title: 'Postupy: přidávání hlaviček a zápatí do dokumentů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete do hlaviček a zápatí v dokumentu přidat text pomocí vlastnosti Headers (záhlaví) a vlastnost zápatí oddílu.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 73844d19ef6bb85c623706ab0d359836e42a3b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828737"
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

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Přidání textu do záhlaví v dokumentu

1. Následující příklad kódu přidá pole pro zobrazení čísla stránky v jednotlivých hlavičkách v dokumentu a pak nastaví zarovnání odstavce tak, aby text byl zarovnán napravo od záhlaví.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>Doplňky VSTO
 Chcete-li použít následující příklady kódu, spusťte je z `ThisAddIn` třídy v projektu.

### <a name="to-add-text-to-footers-in-a-document"></a>Přidání textu do zápatí v dokumentu

1. Následující příklad kódu nastaví písmo textu, který má být vložen do primárního zápatí každého oddílu dokumentu, a poté vloží text do zápatí. Tento příklad kódu používá aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Přidání textu do záhlaví v dokumentu

1. Následující příklad kódu přidá pole pro zobrazení čísla stránky v jednotlivých hlavičkách v dokumentu a pak nastaví zarovnání odstavce tak, aby text byl zarovnán napravo od záhlaví. Tento příklad kódu používá aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Viz také
- [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
