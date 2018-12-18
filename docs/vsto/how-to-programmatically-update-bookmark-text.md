---
title: 'Postupy: programově aktualizovat textu záložky'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efa56c94e211a40e314025ae06d263164de1afd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833015"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Postupy: programově aktualizovat textu záložky
  Můžete vložit text do zástupný symbol záložky v dokumentu aplikace Microsoft Office Word tak, aby text můžete načíst později, nebo k nahrazení textu v záložce. Pokud vyvíjíte přizpůsobení úrovni dokumentu, můžete také aktualizovat text <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek, který je vázán na data. Další informace najdete v tématu [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Záložka objekt může být jeden ze dvou typů:  
  
- A <xref:Microsoft.Office.Tools.Word.Bookmark> hostování ovládacího prvku.  
  
   <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky rozšíření nativní <xref:Microsoft.Office.Interop.Word.Bookmark> objekty povolením vystavení události a datové vazby. Další informace o hostitelských ovládacích prvcích najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
- Nativní <xref:Microsoft.Office.Interop.Word.Bookmark> objektu.  
  
   <xref:Microsoft.Office.Interop.Word.Bookmark> objekty nemají vazby funkcí události nebo data.  
  
  Když přiřadíte text na záložku, chování se liší mezi <xref:Microsoft.Office.Interop.Word.Bookmark> a <xref:Microsoft.Office.Tools.Word.Bookmark>. Další informace najdete v tématu [Bookmark – ovládací prvek](../vsto/bookmark-control.md).  
  
## <a name="use-host-controls"></a>Použití hostitelské ovládací prvky  
  
### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Aktualizovat obsah záložku pomocí ovládací prvek Bookmark  
  
1.  Vytvořit proceduru, která přijímá `bookmark` argument pro název záložky a `newText` argument řetězec, který má přiřadit <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> vlastnost.  
  
    > [!NOTE]  
    >  Přiřazení text, který má <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> nebo <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> vlastnost <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek nezpůsobí záložku, která se má odstranit.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Přiřazení *newText* řetězec, který se <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> vlastnost <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="use-word-objects"></a>Použití objektů aplikace Word  
  
### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Aktualizovat obsah záložku pomocí objektem Wordové záložky  
  
1.  Vytvořit proceduru, která má `bookmark` argument název <xref:Microsoft.Office.Interop.Word.Bookmark>a `newText` argument řetězec, který má přiřadit <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost záložky.  
  
    > [!NOTE]  
    >  Přiřazení text do nativní aplikace Word <xref:Microsoft.Office.Interop.Word.Bookmark> objekt způsobí, že na záložku, která se má odstranit.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Přiřazení *newText* řetězec, který se <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost záložky, který automaticky odstraní záložky. Potom je znovu přidat záložku na <xref:Microsoft.Office.Interop.Word.Bookmarks> kolekce.  
  
     Následující příklad kódu je možné v přizpůsobení na úrovni dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     Následující příklad kódu je možné v doplňku VSTO. Tento příklad používá aktivní dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
 [BOOKMARK – ovládací prvek](../vsto/bookmark-control.md)  
  
  