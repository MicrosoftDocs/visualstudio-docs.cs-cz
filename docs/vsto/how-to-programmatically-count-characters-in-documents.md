---
title: 'Postupy: počítání znaků v dokumentech prostřednictvím kódu programu'
description: Zjistěte, jak lze určit počet znaků v dokumentu pomocí vlastnosti Count kolekce znaků.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824000"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Postupy: počítání znaků v dokumentech prostřednictvím kódu programu
  První znak v dokumentu je na pozici 0, která představuje bod vložení. Poslední pozice znaku je rovna celkovému počtu znaků v dokumentu. Počet znaků v dokumentu můžete určit pomocí <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Characters> kolekce.

 Započítávají se všechny znaky v dokumentu, včetně mezer, značek a dalších znaků, které jsou normálně skryté. I nový prázdný dokument vrátí počet jednoho znaku, protože obsahuje znak odstavce.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Zobrazení počtu znaků v přizpůsobení na úrovni dokumentu

1. Vyberte celý dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. Zobrazí počet znaků v dokumentu v okně se zprávou.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Zobrazení počtu znaků v doplňku VSTO

1. Vyberte celý dokument. Následující příklad vybere aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. Zobrazí počet znaků v dokumentu v okně se zprávou.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>Viz také
- [Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
