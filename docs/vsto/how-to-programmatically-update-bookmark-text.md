---
title: 'Postupy: aktualizace textu záložek prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově vkládat text do zástupné záložky v dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826197"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Postupy: aktualizace textu záložek prostřednictvím kódu programu
  Text můžete vložit do zástupné záložky v dokumentu systém Microsoft Office Word, abyste mohli text později načíst nebo nahradit text na záložce. Pokud vyvíjíte přizpůsobení na úrovni dokumentu, můžete také aktualizovat text v <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacím prvku, který je svázán s daty. Další informace najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Objekt Bookmark může být jeden ze dvou typů:

- <xref:Microsoft.Office.Tools.Word.Bookmark>Hostitelský ovládací prvek.

   <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky rozšiřuje nativní <xref:Microsoft.Office.Interop.Word.Bookmark> objekty tím, že povolují datové vazby a zpřístupňují události. Další informace o hostitelských ovládacích prvcích naleznete v tématu Přehled hostitelských [položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

- Nativní <xref:Microsoft.Office.Interop.Word.Bookmark> objekt.

   <xref:Microsoft.Office.Interop.Word.Bookmark> objekty nemají události nebo funkce datové vazby.

  Když přiřadíte text k záložce, chování se liší mezi <xref:Microsoft.Office.Interop.Word.Bookmark> a a <xref:Microsoft.Office.Tools.Word.Bookmark> . Další informace naleznete v tématu [ovládací prvek Bookmark](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Použití hostitelských ovládacích prvků

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Aktualizace obsahu záložky pomocí ovládacího prvku záložky

1. Vytvořte proceduru, která převezme `bookmark` argument pro název záložky, a `newText` argument pro řetězec, který má být přiřazen <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> Vlastnosti.

    > [!NOTE]
    > Přiřazení textu k <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> vlastnosti nebo <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku nezpůsobí odstranění záložky.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. Přiřaďte řetězec *NewText* k <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Použití objektů aplikace Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Aktualizace obsahu záložky pomocí objektu Word Bookmark

1. Vytvořte proceduru, která má `bookmark` argument pro název <xref:Microsoft.Office.Interop.Word.Bookmark> , a `newText` argument pro řetězec, který má být přiřazen <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Vlastnosti záložky.

    > [!NOTE]
    > Při přiřazování textu k nativnímu objektu aplikace Word <xref:Microsoft.Office.Interop.Word.Bookmark> dojde k odstranění záložky.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. Přiřaďte řetězec *NewText* k <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Vlastnosti záložky, která automaticky odstraní záložku. Pak záložku znovu přidejte do <xref:Microsoft.Office.Interop.Word.Bookmarks> kolekce.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     V doplňku VSTO se dá použít následující příklad kódu. Tento příklad používá aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>Viz také
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Ovládací prvek záložek](../vsto/bookmark-control.md)
