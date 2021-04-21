---
title: 'Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově ukládat existující dokumenty a nové dokumenty, které ještě nebyly uloženy, do aplikace Microsoft Visio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 340d813a19c0c0dc5c347d3cfe4c7b29ff1bd049
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828992"
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

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>Uložení dokumentu s novým názvem
 Použijte `Microsoft.Office.Interop.Visio.Document.SaveAs` metodu k uložení nového dokumentu nebo dokumentu s novým názvem. Tato metoda vyžaduje, abyste zadali nový název souboru.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Uložení aktivního dokumentu aplikace Visio s novým názvem

- Zavolejte `Microsoft.Office.Interop.Visio.Document.SaveAs` metodu `Microsoft.Office.Tools.Visio.Document` , kterou chcete uložit, pomocí plně kvalifikované cesty, včetně názvu souboru. Pokud soubor s tímto názvem již v této složce existuje, je tiše přepsán.

     Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Uloží dokument s novým názvem a zadanými argumenty.
 Použijte `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodu k uložení dokumentu s novým názvem a zadejte všechny použitelné argumenty, které se mají použít pro dokument.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Uložení dokumentu s novým názvem a zadanými argumenty

- Zavolejte `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodu `Microsoft.Office.Tools.Visio.Document` , kterou chcete uložit, pomocí plně kvalifikované cesty, včetně názvu souboru. Pokud soubor s tímto názvem již v této složce existuje, je vyvolána výjimka.

     Následující příklad kódu uloží aktivní dokument s novým názvem, označí dokument jako jen pro čtení a zobrazí dokument v seznamu naposledy použitých dokumentů. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

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
