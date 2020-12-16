---
title: 'Postupy: odstraňování všech komentářů z dokumentů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově odebrat všechny komentáře z dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdb2d7b61efc1e40bf08b6b38ea6564892a04a33
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526652"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Postupy: odstraňování všech komentářů z dokumentů prostřednictvím kódu programu
  Použijte `DeleteAllComments` metodu k odebrání všech komentářů z systém Microsoft Office wordového dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Odebrání všech komentářů z dokumentu, který je součástí přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> metodu `ThisDocument` třídy v projektu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` třídy.

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Odebrání všech komentářů z dokumentu pomocí doplňku VSTO

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> metodu, <xref:Microsoft.Office.Interop.Word.Document> ze které chcete odebrat komentáře.

     Následující příklad kódu odebere všechny komentáře z aktivního dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>Viz také
- [Postupy: přidávání komentářů k textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Položka hostitele dokumentu](../vsto/document-host-item.md)
