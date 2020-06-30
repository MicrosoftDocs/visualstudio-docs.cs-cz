---
title: 'Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 891a5c44159d10aacbb767cbc5376ae1d62252b0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547053"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu
  Existuje několik způsobů, jak uložit systém Microsoft Office dokumentů aplikace Visio:

- Uloží změny v existujícím dokumentu.

- Uložte nový dokument nebo uložte dokument s novým názvem.

- Uloží dokument se zadanými argumenty.

  Další informace najdete v referenční dokumentaci k jazyku VBA pro [Microsoft.Office.Interop.Visio.Document. Save](/office/vba/api/Visio.Document.Save) – metoda [Microsoft.Office.Interop.Visio.Document. Metoda SaveAs](/office/vba/api/Visio.Document.SaveAs) a [Microsoft.Office.Interop.Visio.Document. Metoda SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx)

## <a name="save-an-existing-document"></a>Uložit existující dokument

### <a name="to-save-a-document"></a>Uložení dokumentu

- Zavolejte `Microsoft.Office.Interop.Visio.Document.Save` metodu `Microsoft.Office.Tools.Visio.Document` třídy dokumentu, který byl dříve uložen.

     Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

    > [!NOTE]
    > `Microsoft.Office.Interop.Visio.Document.Save`Metoda vyvolá výjimku, pokud nový dokument Visia ještě nebyl uložen.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]

## <a name="save-a-document-with-a-new-name"></a>Uložení dokumentu s novým názvem
 Použijte `Microsoft.Office.Interop.Visio.Document.SaveAs` metodu k uložení nového dokumentu nebo dokumentu s novým názvem. Tato metoda vyžaduje, abyste zadali nový název souboru.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Uložení aktivního dokumentu aplikace Visio s novým názvem

- Zavolejte `Microsoft.Office.Interop.Visio.Document.SaveAs` metodu `Microsoft.Office.Tools.Visio.Document` , kterou chcete uložit, pomocí plně kvalifikované cesty, včetně názvu souboru. Pokud soubor s tímto názvem již v této složce existuje, je tiše přepsán.

     Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Uloží dokument s novým názvem a zadanými argumenty.
 Použijte `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodu k uložení dokumentu s novým názvem a zadejte všechny použitelné argumenty, které se mají použít pro dokument.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Uložení dokumentu s novým názvem a zadanými argumenty

- Zavolejte `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodu `Microsoft.Office.Tools.Visio.Document` , kterou chcete uložit, pomocí plně kvalifikované cesty, včetně názvu souboru. Pokud soubor s tímto názvem již v této složce existuje, je vyvolána výjimka.

     Následující příklad kódu uloží aktivní dokument s novým názvem, označí dokument jako jen pro čtení a zobrazí dokument v seznamu naposledy použitých dokumentů. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu vyžaduje následující:

- Chcete-li uložit dokument s novým názvem, adresář s názvem `Test` musí být umístěn ve složce *dokumenty* (pro systém Windows XP a starší) nebo ve složce *dokumenty* (pro systém Windows Vista).

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)
- [Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-close-visio-documents.md)
- [Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-print-visio-documents.md)
