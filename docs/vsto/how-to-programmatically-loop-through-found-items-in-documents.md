---
title: 'Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí programu Visual Studio programově procházet nalezené položky v dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ce3153eb4e2fd7fd44318097a6b76ef6e0346086
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827341"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Word.Find>Třída má <xref:Microsoft.Office.Interop.Word.Find.Found%2A> vlastnost, která vrací **hodnotu true** pokaždé, když se najde hledaná položka. Můžete procházet všemi instancemi, které byly nalezeny v rámci <xref:Microsoft.Office.Interop.Word.Range> pomocí <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Cyklicky nalezené položky

1. Deklarujte <xref:Microsoft.Office.Interop.Word.Range> objekt.

    Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    V doplňku VSTO se dá použít následující příklad kódu. Tento příklad používá aktivní dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. Pomocí <xref:Microsoft.Office.Interop.Word.Find.Found%2A> vlastnosti ve smyčce můžete vyhledat všechny výskyty řetězce v dokumentu a zvýšit celočíselnou proměnnou o 1 při každém nalezení řetězce.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. Zobrazí počet nalezených řetězců v okně se zprávou.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   Následující příklady znázorňují metodu Complete.

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Procházení položek v přizpůsobení na úrovni dokumentu

1. Následující příklad ukazuje kompletní kód pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Procházení položek v doplňku VSTO

1. Následující příklad ukazuje úplný kód doplňku VSTO. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Viz také
- [Postupy: hledání a nahrazování rext v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Postupy: nastavování možností hledání v aplikaci Word prostřednictvím kódu programu](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: obnovení výběru po hledání prostřednictvím kódu programu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
