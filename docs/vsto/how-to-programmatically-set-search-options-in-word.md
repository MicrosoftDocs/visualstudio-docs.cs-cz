---
title: 'Postupy: nastavování možností hledání v aplikaci Word prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově nastavit možnosti hledání pro výběry v Microsoft Wordu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45af6a801a146838919402c31be502cf4825e718
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528556"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Postupy: nastavování možností hledání v aplikaci Word prostřednictvím kódu programu
  Existují dva způsoby, jak nastavit možnosti hledání pro výběry v systém Microsoft Office dokumentů aplikace Word:

- Nastaví jednotlivé vlastnosti <xref:Microsoft.Office.Interop.Word.Find> objektu.

- Použijte argumenty <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> objektu.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Použití vlastností objektu Find
 Následující kód nastaví vlastnosti <xref:Microsoft.Office.Interop.Word.Find> objektu pro hledání textu v rámci aktuálního výběru. Všimněte si, že kritéria hledání, jako je vyhledávání předávaného, zalamování a hledání textu, jsou vlastnosti <xref:Microsoft.Office.Interop.Word.Find> objektu.

 Nastavení jednotlivých vlastností <xref:Microsoft.Office.Interop.Word.Find> objektu není užitečné při psaní kódu jazyka C#, protože je nutné zadat stejné vlastnosti jako parametry v <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodě. Proto tento příklad obsahuje pouze kód Visual Basic.

### <a name="to-set-search-options-using-a-find-object"></a>Nastavení možností vyhledávání pomocí objektu Find

1. Nastavení vlastností <xref:Microsoft.Office.Interop.Word.Find> objektu pro hledání textu po výběru. 

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Použít argumenty metody Execute
 Následující kód používá <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodu <xref:Microsoft.Office.Interop.Word.Find> objektu pro hledání textu v rámci aktuálního výběru. Všimněte si, že kritéria hledání, jako je například vyhledávání předávaného, zalamování a hledání textu, jsou předána jako parametry <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Nastavení možností vyhledávání pomocí argumentů spustit metodu

1. Předání vyhledávacích kritérií jako parametrů <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody pro hledání textu po výběru. 

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Viz také
- [Postupy: hledání a nahrazování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Postupy: obnovení výběru po hledání prostřednictvím kódu programu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
