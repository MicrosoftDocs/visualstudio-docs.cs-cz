---
title: 'Postupy: používání předdefinovaných dialogových oken v aplikaci Word prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f5ee28b0296037b9b5490ca691a27d613c793228
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675907"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Postupy: používání předdefinovaných dialogových oken v aplikaci Word prostřednictvím kódu programu
  Při práci s Microsoft Office Word, jsou časy, kdy je třeba zobrazit dialogová okna pro uživatelský vstup. Přestože je možné vytvořit vlastní, můžete také chtít postup používání předdefinovaných dialogových oknech v aplikaci Word, které jsou přístupné na <xref:Microsoft.Office.Interop.Word.Dialogs> kolekce <xref:Microsoft.Office.Interop.Word.Application> objektu. Umožňuje získat přístup k více než 200 předdefinovaných dialogových oknech, které jsou reprezentovány jako výčty.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="display-dialog-boxes"></a>Zobrazování dialogových oken  
 Chcete-li zobrazit dialogové okno, použijte jednu z hodnot <xref:Microsoft.Office.Interop.Word.WdWordDialog> výčet k vytvoření <xref:Microsoft.Office.Interop.Word.Dialog> objekt, který reprezentuje dialogových oken, které chcete zobrazit. Potom zavolejte <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodu <xref:Microsoft.Office.Interop.Word.Dialog> objektu.  
  
 Následující příklad kódu ukazuje, jak zobrazit **otevřít soubor** dialogové okno. Pokud chcete použít tento příklad, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Přístup dialogové okno pole členů, které jsou k dispozici prostřednictvím pozdní vazby  
 Některé vlastnosti a metody dialogových oken v aplikaci Word jsou k dispozici pouze prostřednictvím pozdní vazby. Projekty v jazyce Visual Basic, kde **Option Strict** zapnutý, je nutné použít pro přístup k těmto členům reflexe. Další informace najdete v tématu [pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).  
  
 Následující příklad kódu ukazuje, jak používat **název** vlastnost **otevřít soubor** dialogové okno v jazyce Visual Basic, projekty, kde **Option Strict** vypnutý nebo v jazyce Visual C# projekty, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pokud chcete použít tento příklad, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Následující příklad kódu ukazuje, jak používat reflexi k přístupu **název** vlastnost **otevřít soubor** dialogové okno v jazyce Visual Basic, projekty, kde **Option Strict** je na. Pokud chcete použít tento příklad, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: používání dialogových oken aplikace Word ve skrytém režimu prostřednictvím kódu programu](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexe (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexe (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  