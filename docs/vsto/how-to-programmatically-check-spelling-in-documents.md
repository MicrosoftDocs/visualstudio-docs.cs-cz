---
title: 'Postupy: Kontrola pravopisu v dokumentech prostřednictvím kódu programu'
description: Přečtěte si, že pokud chcete v dokumentu programově kontrolovat pravopis, můžete použít metodu CheckSpelling.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7e04c542f91b9d7675eb81e7a3178e3427c52a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828849"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Postupy: Kontrola pravopisu v dokumentech prostřednictvím kódu programu
  Chcete-li kontrolovat pravopis v dokumentu, použijte <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodu. Tato metoda vrací logickou hodnotu, která označuje, zda je zadaný parametr správně zadán.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Kontrola pravopisu a zobrazení výsledků v okně se zprávou

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodu a předejte jí rozsah textu pro kontrolu pravopisu chyb. Chcete-li použít tento příklad kódu, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet113":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet113":::

## <a name="see-also"></a>Viz také
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
