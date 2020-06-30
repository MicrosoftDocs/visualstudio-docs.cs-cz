---
title: 'Postupy: přidávání komentářů k textu v dokumentech prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88350a0fb50c1d5feb0eba9706ef5b6ad56fd9df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538110"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Postupy: přidávání komentářů k textu v dokumentech prostřednictvím kódu programu
  Vlastnost Comments třídy Document přidá komentář k oblasti textu v dokumentu aplikace systém Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Následující příklad přidá komentář k prvnímu odstavci v dokumentu.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Přidání nového komentáře k textu v přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodu <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> vlastnosti a zadejte rozsah a text komentáře. Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Přidání nového komentáře k textu v doplňku VSTO

1. Zavolejte <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodu <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> vlastnosti a zadejte rozsah a text komentáře.

     Následující příklad kódu přidá komentář k aktivnímu dokumentu. Chcete-li použít tento příklad, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Robustní programování
 Chcete-li změnit iniciály uživatele, které Word přičítá k komentářům, použijte <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> vlastnost.

## <a name="see-also"></a>Viz také
- [Postupy: odstraňování všech komentářů z dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Položka hostitele dokumentu](../vsto/document-host-item.md)
