---
title: 'Postupy: Programové použití dialogových oken aplikace Word ve skrytém režimu'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255851"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Postupy: Programové použití dialogových oken aplikace Word ve skrytém režimu
  Můžete provádět komplexní operace s jedním voláním metody vyvoláním vestavěných dialogových oken v aplikaci systém Microsoft Office Word bez jejich zobrazení uživateli. To lze provést pomocí <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> objektu bez volání <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Příklady
 Následující příklady kódu ukazují, jak použít dialogové okno **nastavení stránky** v skrytém režimu k nastavení více vlastností nastavení stránky bez zásahu uživatele. V příkladech se <xref:Microsoft.Office.Interop.Word.Dialog> pomocí objektu konfiguruje vlastní velikost stránky. Konkrétní nastavení pro nastavení stránky, například horní okraj, dolní okraj atd., jsou k dispozici jako vlastnosti <xref:Microsoft.Office.Interop.Word.Dialog> s pozdní vazbou objektu. Tyto vlastnosti jsou v době běhu dynamicky vytvářeny slovem.

 Následující příklad ukazuje, jak provést tuto úlohu v Visual Basic projektů, kde **Option Strict** je off a v vizuálních C# projektech cílících [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]na. V těchto projektech můžete použít funkce pozdní vazby v Visual Basic a vizuálních C# kompilátorech. Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Následující příklad ukazuje, jak provést tuto úlohu v Visual Basic projekty, kde je **možnost Option Strict** zapnutá. V těchto projektech je nutné použít reflexi pro přístup k vlastnostem s pozdní vazbou. Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Viz také:
- [Postupy: Programové použití vestavěných dialogových oken ve Wordu](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexe (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexe (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
