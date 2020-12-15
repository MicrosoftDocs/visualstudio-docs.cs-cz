---
title: 'Postupy: používání dialogových oken aplikace Word ve skrytém režimu prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově používat dialogová okna aplikace Microsoft Word ve skrytém režimu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 263041fe15f07e8041bb771a6f3abd8b3311b0f2
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523167"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Postupy: používání dialogových oken aplikace Word ve skrytém režimu prostřednictvím kódu programu
  Můžete provádět komplexní operace s jedním voláním metody vyvoláním vestavěných dialogových oken v aplikaci systém Microsoft Office Word bez jejich zobrazení uživateli. To lze provést pomocí <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> objektu bez volání <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Příklady
 Následující příklady kódu ukazují, jak použít dialogové okno **nastavení stránky** v skrytém režimu k nastavení více vlastností nastavení stránky bez zásahu uživatele. V příkladech se pomocí <xref:Microsoft.Office.Interop.Word.Dialog> objektu konfiguruje vlastní velikost stránky. Konkrétní nastavení pro nastavení stránky, například horní okraj, dolní okraj atd., jsou k dispozici jako vlastnosti s pozdní vazbou <xref:Microsoft.Office.Interop.Word.Dialog> objektu. Tyto vlastnosti jsou v době běhu dynamicky vytvářeny slovem.

 Následující příklad ukazuje, jak provést tuto úlohu v projektech Visual Basic, kde **Option Strict** je off a v projektech Visual C#, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . V těchto projektech můžete použít funkce pozdní vazby v kompilátorech Visual Basic a Visual C#. Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Následující příklad ukazuje, jak provést tuto úlohu v Visual Basic projekty, kde je **možnost Option Strict** zapnutá. V těchto projektech je nutné použít reflexi pro přístup k vlastnostem s pozdní vazbou. Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Viz také
- [Postupy: používání předdefinovaných dialogových oken v aplikaci Word prostřednictvím kódu programu](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexe (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexe (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
