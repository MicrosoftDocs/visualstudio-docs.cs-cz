---
title: 'Postupy: otevírání existujících dokumentů prostřednictvím kódu programu'
description: Naučte se používat metodu Open k otevření existujícího dokumentu Microsoft Wordu, který je určený plně kvalifikovanou cestou a názvem souboru.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525557"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Postupy: otevírání existujících dokumentů prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Metoda otevře existující systém Microsoft Office wordový dokument určený plně kvalifikovanou cestou a názvem souboru. Tato metoda vrátí <xref:Microsoft.Office.Interop.Word.Document> , který představuje otevřený dokument.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Otevření dokumentu

- Zavolejte <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodu <xref:Microsoft.Office.Interop.Word.Documents> kolekce a zadejte cestu k dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Otevření dokumentu jen pro čtení

- Zavolejte <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodu, zadejte cestu k dokumentu a nastavte argument *ReadOnly* na **hodnotu true** ve volání metody.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu vyžaduje následující:

- Dokument s názvem *NewDocument.doc* musí existovat v adresáři s názvem *test* na jednotce C.

## <a name="see-also"></a>Viz také
- [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md)
- [Postupy: zavírání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
