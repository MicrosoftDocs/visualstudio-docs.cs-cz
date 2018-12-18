---
title: 'Postupy: přidávání komentáře k textu dokumentů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ca0d15ee69bb58aae765c03c1233a78bfeeb119c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675692"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Postupy: přidávání komentáře k textu dokumentů prostřednictvím kódu programu
  Vlastnosti komentáře dokumentu třídy přidá komentář na rozsah textu do dokumentu aplikace Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Následující příklad přidá komentář do prvního odstavce v dokumentu.  
  
## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Chcete-li přidat nový komentář na text v přizpůsobení na úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodu <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> vlastnost a zadejte rozsah a text komentáře. Pokud chcete použít následující příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Chcete-li přidat nový komentář na text v doplňku VSTO  
  
1.  Volání <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodu <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> vlastnost a zadejte rozsah a text komentáře.  
  
     Následující příklad kódu přidá komentář do aktivního dokumentu. Pokud chcete použít tento příklad, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Chcete-li změnit iniciály uživatele, které aplikace Word přidá do komentáře, použijte <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Programová odstraňování všech komentářů z dokumentů](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Hostitelská položka Document](../vsto/document-host-item.md)  
  
  