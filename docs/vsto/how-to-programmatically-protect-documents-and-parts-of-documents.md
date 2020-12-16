---
title: Ochrana dokumentů a částí dokumentů prostřednictvím kódu programu
description: Zjistěte, jak můžete přidat ochranu do dokumentů aplikace Microsoft Word a zabránit tak uživatelům v provádění úprav v dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1dbb001a8c350b376f30047dbafbf747f043e91d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527761"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Postupy: ochrana dokumentů a částí dokumentů prostřednictvím kódu programu
  Můžete přidat ochranu systém Microsoft Office dokumentů aplikace Word a zabránit tak uživatelům v provádění úprav v dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Můžete také označit některé oblasti dokumentu jako výjimky, aby určení uživatelé mohli upravovat pouze ty oblasti dokumentu. Můžete například chtít chránit celý dokument s výjimkou konkrétní záložky. Volitelně můžete přidat heslo, aby uživatelé nedokázali ochranu dokumentu odebrat, pokud neznají heslo.

> [!NOTE]
> Následující příklad nepoužívá ochranu heslem. je však vhodné zvážit použití hesla při přidávání ochrany dokumentu. Další informace najdete v tématu Ukázka ochrany dokumentů v [ukázkách vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

 Můžete také použít ovládací prvky obsahu k ochraně částí dokumentů. Další informace najdete v tématu [Postupy: Ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Ochrana dokumentu, který je součástí přizpůsobení na úrovni dokumentu

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Ochrana dokumentu, který je součástí přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metodu `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Vyloučení ovládacího prvku Záložka z ochrany dokumentu

1. Chraňte celý dokument pomocí <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

2. Vylučte `Bookmark1` z ochrany dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]

### <a name="compile-the-code"></a>Kompilovat kód
 Chcete-li použít tyto příklady kódu, spusťte je z `ThisDocument` třídy v projektu. Tyto příklady kódu předpokládají, že máte existující <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek s názvem `Bookmark1` v dokumentu, ve kterém se zobrazuje tento kód.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Ochrana dokumentu pomocí doplňku VSTO

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Ochrana dokumentu pomocí doplňku VSTO na úrovni aplikace

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> metodu, kterou chcete <xref:Microsoft.Office.Interop.Word.Document> chránit.

     Následující příklad kódu chrání aktivní dokument. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]

## <a name="see-also"></a>Viz také
- [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)
- [Postupy: povolení spuštění kódu na pozadí dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
