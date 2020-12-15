---
title: 'Postupy: používání předdefinovaných dialogových oken v aplikaci Word prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově používat integrovaná dialogová okna v aplikaci Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b2c1a748d38c2b649705fa1ad2de21553b710634
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523622"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Postupy: používání předdefinovaných dialogových oken v aplikaci Word prostřednictvím kódu programu
  Při práci s systém Microsoft Office Wordem existují situace, kdy je potřeba zobrazit dialogová okna pro vstup uživatele. I když můžete vytvořit vlastní, můžete také chtít vzít v úvahu přístup k používání vestavěných dialogových oken ve Wordu, které jsou přístupné v <xref:Microsoft.Office.Interop.Word.Dialogs> kolekci <xref:Microsoft.Office.Interop.Word.Application> objektu. To vám umožní přístup přes 200 z vestavěných dialogových oken, které jsou reprezentovány jako výčty.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Zobrazit dialogová okna
 Chcete-li zobrazit dialogové okno, použijte jednu z hodnot <xref:Microsoft.Office.Interop.Word.WdWordDialog> výčtu k vytvoření <xref:Microsoft.Office.Interop.Word.Dialog> objektu, který představuje dialogové okno, které chcete zobrazit. Pak zavolejte <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodu <xref:Microsoft.Office.Interop.Word.Dialog> objektu.

 Následující příklad kódu ukazuje, jak zobrazit dialogové okno **otevřít soubor** . Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Přístup k členům dialogového okna, která jsou k dispozici prostřednictvím pozdní vazby
 Některé vlastnosti a metody dialogových oken v aplikaci Word jsou k dispozici pouze prostřednictvím pozdní vazby. V Visual Basic projekty, kde je **možnost Option Strict** zapnuta, je nutné k přístupu k těmto členům použít reflexi. Další informace najdete v tématu [pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).

 Následující příklad kódu ukazuje, jak použít vlastnost **Name** dialogového okna **otevřít** v Visual Basic projekty, kde **Option Strict** je off nebo v projektech Visual C#, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Následující příklad kódu ukazuje, jak použít reflexi pro přístup k vlastnosti **název** dialogového okna **otevření souboru** v Visual Basic projekty, kde **Option Strict** je on. Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Viz také
- [Postupy: používání dialogových oken aplikace Word ve skrytém režimu prostřednictvím kódu programu](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexe (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexe (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
